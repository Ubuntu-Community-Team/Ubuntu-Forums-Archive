---
title: "Passing keyboard inputs to a command"
date: 2013-05-18
forum: General Help
---

### Post by muhammed irshad on 2013-05-18
Hi All,

Is there a way we can pass the inputs needed for a command explicitly in any way in a shell script ? 
Herd inputs of a shell commands are taken from stdin and it is connected to key board . 
For eg : 
' sudo bash ' command will ask you for password . How can i add this into a shell script by passing the input as well 
In one site i have seen that the command  
echo myPassword | sudo -S ls /tmp 
will take the myPassword as password for the command sudo -S ls /tmp . But i am getting myPassword command not found 

Can any one help me ?

---

### Post by dragonfly41 on 2013-05-18
I would try installing AutoKey from repo and try that with your bash scripts ..

[http://ostatic.com/blog/automating-the-linux-desktop-with-autokey](http://ostatic.com/blog/automating-the-linux-desktop-with-autokey)

---

### Post by CaptainMark on 2013-05-19
What are you trying to do exactly, when I want a command or script to run as root on boot I write the script assuming I already have root privilidges and add a line to /etc/rc.local to run the script, if its just a single short command then just add it straight into /etc/rc.local anything in there will be run by root after startup

Just make sure you add it before the exit 0 part or it wont be run

---

### Post by muhammed irshad on 2013-05-28
@[COLOR=#000000]CaptainMark : [/COLOR]Thanks a lot for the reply

>> [COLOR=#000000]What are you trying to do exactly
[/COLOR]
[COLOR=#000000]Say i have to connect to my server with ip as IP and username as user and password for the user be 123 [/COLOR]
[COLOR=#000000]I can connect  using ssh by typing command  'ssh -p 8080 user@IP ' when we type this in terminal we will be prompted for password of the user .[/COLOR]
[COLOR=#000000]  So is there a way i can connect to the client from a shell script by using the ssh command and say i have a file called password which has my password 123 in it . My shell script should connect to the server by taking the password from the file password . [/COLOR]
[COLOR=#000000]Simply i don't want to type the password all the time [/COLOR]

---

### Post by The Cog on 2013-05-28
You can use a bash feature which I think is called here-to. In this example, I have three lines that I pass to the command sort. One of them is a previously allocated shell variable. The line with << sets up the pipe and says that END is the marker for the end of the piped lines (you could use any string you want here). The lines between << END and END are fed to the sort command as its input stream.
```

mySteed=buffalo
sort << END
camel
antelope
$mySteed
END

```
Note that the above won't work with a local sudo command because sudo specifically checks that it's connected to a real keyboard and not a script.

However, if you are doing ssh, you may want to look at passwordless ssh. It involves creating a key on your client and placing that key in the server's list of trusted hosts. [http://usefulubuntu.blogspot.se/2009/03/passwordless-ssh.html](http://usefulubuntu.blogspot.se/2009/03/passwordless-ssh.html)

---

### Post by muhammed irshad on 2013-05-29
@Cog 
Thanks a lot for your reply 
here-to seems to be not working in my case though 

I have a script as below . As you said i am expecting out put as ""User Entered Helloguyz" . But terminal is waiting for user input . And once i give input via keyboard it is giving output as expected. Please help me with this 

#!/bin/bash


read value
<<- END
Helloguyz
END
echo "User Entered "$value

---

### Post by The Cog on 2013-05-29
This line:
```
<<- END
```
doesn't say what program to send the following lines to. I thought you wanted to pipe stuff into a child process.

---

### Post by steeldriver on 2013-05-29
> **muhammed irshad said:**
> 
[COLOR=#000000]Say i have to connect to my server with ip as IP and username as user and password for the user be 123 [/COLOR]
[COLOR=#000000]I can connect  using ssh by typing command  'ssh -p 8080 user@IP ' when we type this in terminal we will be prompted for password of the user .[/COLOR]
[COLOR=#000000]  So is there a way i can connect to the client from a shell script by using the ssh command and say i have a file called password which has my password 123 in it . My shell script should connect to the server by taking the password from the file password . [/COLOR]
[COLOR=#000000]Simply i don't want to type the password all the time [/COLOR]

The correct way to handle that situation imho is to set up key-based authentication (using a key without a passphrase, so you don't need to type anything). If for some reason that option is not available to you then you could use the 'expect' program to run a scripted session.

```
EXPECT(1)                                                                                                                                                           EXPECT(1)

NAME
       expect - programmed dialogue with interactive programs, Version 5

SYNOPSIS
       expect [ -dDinN ] [ -c cmds ] [ [ -[f|b] ] cmdfile ] [ args ]

INTRODUCTION
       Expect is a program that "talks" to other interactive programs according to a script.  Following the script, Expect knows what can be expected from a program and what
       the correct response should be.  An interpreted language provides branching and high-level control structures to direct the dialogue.  In addition, the user can  take
       control and interact directly when desired, afterward returning control to the script.

```

---

