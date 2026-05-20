# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
CLIENT
```
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; 
while True: 
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode())
```
SERVER
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
CLIENT
<img width="1680" height="887" alt="image" src="https://github.com/user-attachments/assets/62a5bb07-0743-40dc-b7e6-00ddd778c7fb" />
SERVER
<img width="1839" height="961" alt="image" src="https://github.com/user-attachments/assets/a6043bc6-0d14-4b20-aa59-6fe7a4482401" />

## PROGRAM - RARP
CLIENT
```
import socket 
s=socket.socket() 
s.bind(('localhost',7000)) 
s.listen(5)
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}; 
while True:
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode())
```
SERVER
```
import socket 
s=socket.socket() 
s.connect(('localhost',7000))
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address", s.recv(1024).decode())
```
## OUPUT -RARP
CLIENT
<img width="1783" height="903" alt="image" src="https://github.com/user-attachments/assets/64319ed1-6692-48f0-92ac-2f0e70076aa5" />
SERVER
<img width="1859" height="900" alt="image" src="https://github.com/user-attachments/assets/94690f10-1c84-42f7-94ec-034872b0c967" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
