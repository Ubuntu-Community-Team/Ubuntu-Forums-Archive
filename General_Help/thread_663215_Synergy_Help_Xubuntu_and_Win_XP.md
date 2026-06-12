---
title: "Synergy Help Xubuntu and Win XP"
date: 2008-01-09
forum: General Help
---

### Post by nazgul42 on 2008-01-09
I am somewhat new to Ubuntu, can use Terminal fine.  How would I set up Synergy with the server on a Win XP PC and Xubuntu being the client? I know it's possible, but I have no idea how.  Thank you for any help at all.

---

### Post by modular9 on 2008-01-13
Running xubuntu ( not bleeding up to the minute version )  

just installed synergy and quick synergy through synaptic ...

Here is my setup

nix : In my accessories section of my menu I now have a quick synergy entry. 

xp : I am using winxp as the server and xubuntu as the client. 
xp : Xp server asked for the screen name which is the computer name of the nix box. 

nix: under the client tab of quick synergy i put the ip address of the xp box. ( screen name did not work ) 

XP : started the server 

Everything works with one caveat at the moment. I can switch from xp to nix but not back . I have to stop the server on nix which "jumps" me back to xp. I am sure this most likely is a setting in my network permissions etc though. 

This setting also works for my ibook as well.

---

### Post by DouglasAWh on 2008-01-29
What if you have DHCP so your IP address changes?  Of course, I am also using two XP boxes at the moment.  Hope to get Ubuntu running on this eventually, but for work purposes XP is better at the moment.

EDIT: I got it working, without the IP address...I actually one of the boxes is Vista.  I wish getting it working on ubuntu was next up on the agenda, but I think I've got some other things I need to do first...

---

### Post by DouglasAWh on 2008-01-29
actually, there is still a problem.  I get the following message in Vista:

[IMG]http://farm3.static.flickr.com/2087/2229054970_06a7f1dedb_o.jpg[/IMG]

It says it's because it's not fully compatible with Vista.  I don't much care.  It works...but I'd like the message to go away, if possible.

---

### Post by modular9 on 2008-01-29
i would think ( never going to use vista so I cant test this ) that this has something to do with the uac settings ? Therefore i think you would need to disable them completely. 

or Synergy under windows has notifications which say something like a small box with the status window and the clients that are connected. I think you can disable this . Also you might want to turn down your log levels to the lowest setting therefore circumventing the need for a popup window to be launched. 

BTW got the switching issue sorted. I have now tattooed right on my right hand and "left" on my left hand :P

---

### Post by DouglasAWh on 2008-01-29
UAC went off as soon as Vista was loaded, so that's not the issue.  

I wouldn't use Vista, except that I am the official Vista tester in my IT department.  Puts me in a good position to complain and push it off as long as possible. :)

---

