---
title: "Transfer folder from mac to ubuntu 16.04.2 LTS"
date: 2017-08-13
forum: General Help
---

### Post by richard7893 on 2017-08-13
Hello 

I have a large folder that I want to transfer from my Mac to my Ubuntu. I have tried following instructions that use the terminal on the Mac, but for some reason it is still not working. 

I am using the scp command on my Mac and use the following syntax:

```

[COLOR=#000000][FONT=Menlo]scp -r /Users/Rich/Desktop/ABR\ Boards 
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]richard7893@ipaddress:/home/richard7893/Desktop[/FONT][/COLOR]
```

and get this error each time 

```
ssh: connect to host 192.168.0.10 port 22: Operation timed out
[COLOR=#000000][FONT=Menlo]lost connection[/FONT][/COLOR]
```

I'm not sure what I am doing wrong. I've used the mac terminal to remotely connect to a linux box before and transferred files back and forth. I'm getting the ipaddress from the ipconfig command on my ubuntu. Am I typing in the wrong path to my Ubuntu? I'm not even prompted to type my password when I use the scp command on the mac terminal. Does anybody know how to fix this? Any help would be appreciated.

---

