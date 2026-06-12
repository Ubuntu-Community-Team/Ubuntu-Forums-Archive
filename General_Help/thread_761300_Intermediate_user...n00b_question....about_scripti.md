---
title: "Intermediate user...n00b question....about scripting"
date: 2008-04-21
forum: General Help
---

### Post by Hickory420 on 2008-04-21
Ok, First and foremost, I want to thank and congratulate the entire Ubuntu support team as I know you guys have your hands VERY full.... constantly. I work in IT so I know the feeling...

Now, what I am trying to do is quite simple to most, and I have a good idea as to what needs to be done.

I have a batch file that (when run in windows xp sp2) it prompts you for an ip address, then tries to ping it, if it pings, then it moves on to the psexec.exe (by sysinternals) command. Psexec.exe executes commands or programs on the computer specified. In my case, I have it copy an executable to the target pc, launches it and at the same time, opens my vnc viewer and connects straight up, no hassles, no questions. works every time. Love It!

Here is my script. (if you decide to use it, please Do Not modify the title :)

```

@echo off

Title Ultr@VNC Single Click... Script written by Hickory420

:start

@echo.

set /p pc=Connect to: 

@echo.

echo Pinging %pc%...

set usr=domain\username
set pwd=password

ping %pc% -n 2 -w 500 | find /I "Reply from" >NUL

If ErrorLevel 1 goto noping

@echo --------------------------

psexec \\%pc% -u %usr% -p %pwd% -c -f -i -d ultravncsc.exe | call "C:\Program Files\UltraVNC\vncviewer.exe" ID:420 -proxy 192.168.xx.xx::5901

@echo --------------------------

@echo.

@echo Closing the VNC connection...

goto Done

:noping

cls

@echo.

@echo Can not Ping Host...

@echo.

goto start

:Done

@echo.

@echo --------------------------

@echo.

@echo Deleting... ultravncsc.exe

del \\%pc%\C$\windows\system32\ultravncsc.exe

@echo.

@echo --------------------------

@echo Done

pause


```

I know that a psexec equivalent is winexe, but I can't seem to compile it :( that's somthing else I have to learn how to do.)
[http://eol.ovh.org/winexe/]("http://eol.ovh.org/winexe/")

I have found a 'Converting DOS Batch Files to Shell Scripts' webpage, but I don't know how to apply it...
[http://www.tldp.org/LDP/abs/html/dosbatch.html]("http://www.tldp.org/LDP/abs/html/dosbatch.html")

I know I can run vncviewer from the terminal and I know I can ping from the terminal. If i can get winexe to work I could use that in place of psexec (or i'll run it with Wine if i have to) So, end of the story, I basically need the batch file to be 'translated' into a shell script (or any script) that I can just double click and punch in the ip address and off i go! just like a batch file :)

I'm not going to touch converting vb scripts!!! That's research for another project.

I am a knowledgeable user and I actually searched the forums before writing this post as i don't really like to post because I like to figure things out for my self (research) but sometimes, only sometimes, someone needs to hold my hand and walk me through it.

Thank you so much for reading!!!


reading other posts on other topics, i have found sooo many people (mostly people who dont try) just begging for help
"I need help with blah, help me"
"ok, do this"
"ok, did that, now what, help me?"
"try this"
"did that too, but this happened, what do I do, help me?"
"Help Yourself! Look It Up!"

lol that was a real post somewhere.

---

