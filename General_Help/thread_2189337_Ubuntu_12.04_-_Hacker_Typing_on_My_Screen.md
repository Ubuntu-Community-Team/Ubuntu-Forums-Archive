---
title: "Ubuntu 12.04 - Hacker Typing on My Screen"
date: 2013-11-21
forum: General Help
---

### Post by dsurfer21 on 2013-11-21
I am 100% certain my machine was hacked.  I am running Ubuntu 12.04 and  had skype open (no connection with anyone) and Firefox, gmail and gchat  in the firefox window and someone started type commands in my window and  in my chat with a friend on my gchat account.  They even typed an obscenity in my chat window!

I opened a command window pressing Alt CTRL T to try and reboot real  fast because when i tried to move the mouse to restart he or she kept moving it  away.  In the terminal window the person kept trying to type this in:   punapmep p-a

I just rebooted my machine.  Is there anything I should do right now?    Reformatting is not an option at this moment because I am traveling   right now and I need a computer to check email consistently.  How can I   find out where the security breach is and how can I stop it right now?


Eventually I just pressed the power button to turn it off and rebooted.

Any advice on what I can or should do? 
Thanks

---

### Post by QIII on 2013-11-21
Are you using an unsecured WiFi hotspot?

---

### Post by dsurfer21 on 2013-11-21
No, not at the moment this happened.  I am using a Wifi connection at a university.

---

### Post by Irihapeti on 2013-11-21
Also, is remote desktop enabled?

---

### Post by dsurfer21 on 2013-11-21
Thanks! I believe remote desktop is enabled.  How can I check?

A few weeks or longer ago I had used remote desktop to log in to an embedded system I was testing for a robotics project.
Is this likely how this hacker got control of my machine?

---

### Post by Irihapeti on 2013-11-21
Type "vino" in a terminal (without the quotes) and it should open the remote desktop control panel. If you're using unity, "remote desktop" or "desktop sharing" should do the same thing. Alternatively, choose desktop sharing preferences (or similar wording) in preferences. I'm a little vague about this because it's one of the first things I remove after doing an install.

This link, although for 11.04, will show you what to look for. [http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/](http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/) In your case, you *don't* want sharing enabled.

From what you've described, I wouldn't be at all surprised to find that you've somehow enabled it.

---

### Post by QIII on 2013-11-21
You should consider your machine well and truly compromised.  Who knows how long you were sidejacked and what session info someone got.  You need to immediately change all passwords all over the web -- AFTER you have a secure, preferably wired, connection on a different machine.

---

### Post by dsurfer21 on 2013-11-21
Thanks!

When I run vino I see:

D-ubuntu:~$ vino
No command 'vino' found, did you mean:
 Command 'pino' from package 'pino' (universe)
 Command 'dino' from package 'dino' (universe)
 Command 'bino' from package 'bino' (universe)
 Command 'kino' from package 'kino' (universe)
 Command 'vina' from package 'autodock-vina' (universe)
 Command 'vinfo' from package 'radiance' (universe)
vino: command not found

When I go into desktop sharing, i did see that enable others to control and see my desktop were selected.  I disabled this right now.  

I definitely need desktop sharing to interface with my robotics prototypes that are running ubuntu on embedded processors.  I was using Remmina to do this.  I am assuming I can still do this succesfully, even after disabling the desktop sharing on this laptop?

Thanks.

---

### Post by 1clue on 2013-11-21
About the security at the time of this incident:
[LIST=1]
[*]Were you in a public space?  Meaning, did somebody have a chance to see your screen as this happened, and/or could they have seen you type the password to your computer?
[*]Is your password easily guessable by somebody who knows who you are?
[LIST=1]
[*]Some part of your name, or the name of someone important to you?
[*]Otherwise based on personal information or favorite themes?
[*]A simple word?
[/LIST]

[*]Could there have been a witness from a previous session who could see the screen, or who knows the password to your RDP?
[/LIST]


What is the output of [B]netstat -tunlp
[/B]
By needing desktop sharing, you mean you use this machine to access others using remote desktop, or that other machines access your machine?  In any of this, do you have an unprotected password or saved password?

---

### Post by dsurfer21 on 2013-11-21
Thanks 1clue.

Basically I have some ebedded processors running on some robotic hardware.  I want to see the camera feed that is on the robot so I use desktop sharing and remmina to login from my laptop and see the screen on the robot's ubuntu setup and to see the video feed in the desktop.  I do not need for the embedded processors to access my laptop's desktop.  Therefore I am guessing that disabling the desktop sharing as I just did , will still allow me to control the embedded processor's desktop.


Nobody would have seen my password in person or guessed it easily.  Over the last week and a half I was in a hotel using the wifi, and then at starbucks briefly.  Since then I have used wifi in a university office room.  

I will look for a wired connection here at the university and change all my web passwords just to be careful.  I'm not sure what else I can or should do?  I was hoping to avoid a reformat.  Is this necessary?

I think this happened today as far as someone accesing my machine.  They were fooling around and typing messages in my gchat session with my friend like "suck my ****" and other immature things.  I wonder if they were not really trying to do anything harmful other than fool around but I don't know.  I am not sure if this person likely is on the wifi network here at the university and is just fooling around?  This happened while I was on the university's wifi network this afternoon.

I am running skype right now.

Here is what **netstat -tunlp **shows:

@D-ubuntu:~$ netstat -tunlp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:44052           0.0.0.0:*               LISTEN      3793/skype      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:44471           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:44052           0.0.0.0:*                           3793/skype      
udp        0      0 127.0.0.1:53            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 127.0.0.1:52400         0.0.0.0:*                           3793/skype      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp6       0      0 :::55253                :::*                                -               
udp6       0      0 :::5353                 :::*                                -

---

### Post by 1clue on 2013-11-21
Do you know if the embedded processors involved support an encrypted RDP session?  Or more to the point, that you actually used an encrypted stream?

BTW, if you can wrap that netstat -tunlp in a code block I'll be able to read it more easily.

Back when I was in college in the late '80s the world was different, but I doubt college kids are much different.  In a world with Commodore 64's and Atari CoCos and the like, we used to crack into each other's systems all the time.  This was just friends playing around, what are you going to get when you crack a Commodore 64?  The Internet was there, but we couldn't hook up to it on our personal hardware, we had to use the mainframe.  My college had a phone hookup for it, but nobody could get the number and nobody dared mess with it anyway.  Nobody worried about serious consequences with this sort of thing, and I'm glad I got it out of my system back when it was still fun for everyone.

I remember one session on the mainframe (CDC Cyber 170) I had an experience similar to yours.  I thought something nefarious was happening, but it was the guy next to me using a terminal-to-terminal messaging tool to print things on my screen.  I typed the responses back, and he just looked over at my terminal to see what I was saying.  I was completely freaked.  I found out about a week later what might have happened, and then talked to the guy who had been on my left.  He was so ... giddy ... and even more so when I figured it out.

Regardless, you're on a college network.  Somebody with a packet sniffer wouldn't find it too hard to look for unencrypted passwords.  It could be just some guy messing with you.  If you can figure that out, you may save your system.

Seriously, if this is a real intrusion rather than some guy you know messing with you (even from your home somewhere) then I've never been able to be confident after that.  I know a whole lot more about security and a little more about cleanup than I used to, but the thing is if somebody is that adept at getting in, they're quite likely more adept at staying in than I am at getting everything cleaned off.

That's not what you want to hear, but you gotta think about it in a way that makes sense.

---

### Post by dsurfer21 on 2013-11-21
> **1clue said:**
> Do you know if the embedded processors involved support an encrypted RDP session?  Or more to the point, that you actually used an encrypted stream?

BTW, if you can wrap that netstat -tunlp in a code block I'll be able to read it more easily.

Back when I was in college in the late '80s the world was different, but I doubt college kids are much different.  In a world with Commodore 64's and Atari CoCos and the like, we used to crack into each other's systems all the time.  This was just friends playing around, what are you going to get when you crack a Commodore 64?  The Internet was there, but we couldn't hook up to it on our personal hardware, we had to use the mainframe.  My college had a phone hookup for it, but nobody could get the number and nobody dared mess with it anyway.  Nobody worried about serious consequences with this sort of thing, and I'm glad I got it out of my system back when it was still fun for everyone.

I remember one session on the mainframe (CDC Cyber 170) I had an experience similar to yours.  I thought something nefarious was happening, but it was the guy next to me using a terminal-to-terminal messaging tool to print things on my screen.  I typed the responses back, and he just looked over at my terminal to see what I was saying.  I was completely freaked.  I found out about a week later what might have happened, and then talked to the guy who had been on my left.  He was so ... giddy ... and even more so when I figured it out.

Regardless, you're on a college network.  Somebody with a packet sniffer wouldn't find it too hard to look for unencrypted passwords.  It could be just some guy messing with you.  If you can figure that out, you may save your system.

Seriously, if this is a real intrusion rather than some guy you know messing with you (even from your home somewhere) then I've never been able to be confident after that.  I know a whole lot more about security and a little more about cleanup than I used to, but the thing is if somebody is that adept at getting in, they're quite likely more adept at staying in than I am at getting everything cleaned off.

That's not what you want to hear, but you gotta think about it in a way that makes sense.


Thanks 1clue.

Those are really cool stories you have from when you were in college.

I  set up the ubuntu installations on the embedded processors for the  robotic prototypes.  I don't remember setting anything up for it to  support an encrypted RDP session but I will have to check that out.  I  know I have to type in a password that I set up in order to use remote  desktop on those prototypes.  Nobody else has been using them except for  me.

Do you know if there is anything I can check to make sure  this person was just messing with me and didn't try to take over my  system as well?


Here is the netstat code block:
```
D-ubuntu:~$ netstat -tunlp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:44052           0.0.0.0:*               LISTEN      3793/skype      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:44471           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:44052           0.0.0.0:*                           3793/skype      
udp        0      0 127.0.0.1:53            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 127.0.0.1:52400         0.0.0.0:*                           3793/skype      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp6       0      0 :::55253                :::*                                -               
udp6       0      0 :::5353                 :::*                                -        

```

Here it is again with sudo netstat -lp

```
@D-ubuntu:~$ sudo netstat -tunlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:44052           0.0.0.0:*               LISTEN      3793/skype      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1550/dnsmasq    
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN      1030/xrdp-sesman
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      521/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      595/cupsd       
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN      1028/xrdp       
tcp6       0      0 :::22                   :::*                    LISTEN      521/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      595/cupsd       
udp        0      0 0.0.0.0:44471           0.0.0.0:*                           584/avahi-daemon: r
udp        0      0 0.0.0.0:44052           0.0.0.0:*                           3793/skype      
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1550/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1454/dhclient   
udp        0      0 127.0.0.1:52400         0.0.0.0:*                           3793/skype      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           584/avahi-daemon: r
udp6       0      0 :::55253                :::*                                584/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                584/avahi-daemon: r


```

---

### Post by 1clue on 2013-11-21
OK so you can definitely do without anything in that list that says 'xrdp' in the last column.  Xrdp is what you put on the other boxes.  If you have no reason to use a Windows box to connect to your Linux box, then you should not have that stuff running on your workstation.

As well, I'd make sure your ~/.ssh/authorized_keys* files are empty for that box too.  That's one way somebody could get in and do anything they want.

I'm pretty sure what happened based on the above info is that somebody hacked your xrdp server.  Nothing else explains why you could see them moving or typing, and how they could move the pointer to keep you from hitting a button.  If your password is the same as any of those other boxes, that's a way for them to get access.

In any case, the guy was clearly messing with you because he knew you were watching and deliberately baited you.  Whether the guy had a grudge or not, or a nefarious purpose, that's for you to figure out.

---

### Post by jamesisin on 2013-11-22
Maybe I'm missing something here but why do we believe anyone was controlling this machine?  It seems this could just as readily be explained by random keyboard/mouse behavior.  The letters typed aren't anything like any command, and the mouse movement also lacked any articulable purpose.  What is the evidence which shows the machine in question was under remote control?

---

### Post by QIII on 2013-11-22
In part because before it was edited, the OP's first post indicated that someone was causing rude and vulgar statements to appear in messages they were typing into a chat client.

---

### Post by dsurfer21 on 2013-11-22
> **jamesisin said:**
> Maybe I'm missing something here but why do we believe anyone was controlling this machine?  It seems this could just as readily be explained by random keyboard/mouse behavior.  The letters typed aren't anything like any command, and the mouse movement also lacked any articulable purpose.  What is the evidence which shows the machine in question was under remote control?

Yes basically I had firefox open and gmail in one of the tabs open.  I can use gchat from my gmail window and I was chatting with my girlfriend when all the sudden i see my cursor move and this person was pressing backspace when I tried to type messages in to my girlfriend.  Eventually he/she started typing vulgar statements and then some funny things.  Then we fought over the keyboard control and i just turned the laptop off and restarted.

So far I have not seen any more of this behavior since it happened about 5 hours ago.

I wonder if it was just another student in the network or even in the lab I was in who could access my desktop.

---

### Post by dsurfer21 on 2013-11-22
> **1clue said:**
> OK so you can definitely do without anything in that list that says 'xrdp' in the last column.  Xrdp is what you put on the other boxes.  If you have no reason to use a Windows box to connect to your Linux box, then you should not have that stuff running on your workstation.

As well, I'd make sure your ~/.ssh/authorized_keys* files are empty for that box too.  That's one way somebody could get in and do anything they want.

I'm pretty sure what happened based on the above info is that somebody hacked your xrdp server.  Nothing else explains why you could see them moving or typing, and how they could move the pointer to keep you from hitting a button.  If your password is the same as any of those other boxes, that's a way for them to get access.

In any case, the guy was clearly messing with you because he knew you were watching and deliberately baited you.  Whether the guy had a grudge or not, or a nefarious purpose, that's for you to figure out.

Thanks 1clue.  Would I need to go and manually uninstall xrdp or how would I stop if from running anymore on my workstation?  I needed xrdp on the embedded processors because sometimes I would login from a windows laptop to control the desktop on them.  I do not need to access this laptop remotely.

Do I need to manually edit the authorized_keys file and take out any lines that are related to xrdp?

I don't know anyone who would have done this purposely if they knew who I was... If someone saw my machine pop up on the university network then I could see them having a little fun with me..  I'm not sure if there is any way to find out if it was someone on the network.  I would feel many times better since it wasn't someone deliberately hacking, rather most likely just a college student having fun at my expense :-)

Also I had answered another question in another post.  When I went into desktop sharing just a little while ago, i did see that enable others to control  and see my desktop were selected.  The option to require a password was not selected either.  I disabled desktop sharing though a little after seeing that this evening after the incident with the person taking over my desktop.

---

### Post by jamesisin on 2013-11-22
I shall be very interested to discover how this control was gained then.

---

### Post by 1clue on 2013-11-22
> **dsurfer21 said:**
> Thanks 1clue.  Would I need to go and manually uninstall xrdp or how would I stop if from running anymore on my workstation?  I needed xrdp on the embedded processors because sometimes I would login from a windows laptop to control the desktop on them.  I do not need to access this laptop remotely.


Yes.  You would use rdesktop or some other remote desktop CLIENT on your workstation.  Xrdp is a server.  You don't need it, and as you noticed it can be used to do bad things.

IMO if these are Linux-based clients I would use something besides rdp to access them, unless some Windows users are hitting these same boxes.  I'd use ssh -X <box> and then start up any X-related apps individually.

> 
Do I need to manually edit the authorized_keys file and take out any lines that are related to xrdp?


authorized_keys2 has nothing to do with rdesktop.  It has to do with ssh.  It allows remote clients specified in the file to connect to your laptop, possibly without a password.  It's for lazy people.  (that's not entirely fair, it CAN be used to enhance security but that's not how it's usually used)

If nobody should be logging into that box remotely, then just delete the file.

> 
I don't know anyone who would have done this purposely if they knew who I was... If someone saw my machine pop up on the university network then I could see them having a little fun with me..  I'm not sure if there is any way to find out if it was someone on the network.  I would feel many times better since it wasn't someone deliberately hacking, rather most likely just a college student having fun at my expense :-)

Also I had answered another question in another post.  When I went into desktop sharing just a little while ago, i did see that enable others to control  and see my desktop were selected.  The option to require a password was not selected either.  I disabled desktop sharing though a little after seeing that this evening after the incident with the person taking over my desktop.

Live and learn.  Don't put unauthenticated services on the network, even at home.  It leads to some really bad habits. that could get you in serious trouble.

What you did is open the door and let anyone walk in and use your stuff.  You need to ask yourself how many times something like this has happened when you weren't watching.  Do you keep any personal information on this system?  You need to consider that to be compromised.

IMO you need to reinstall that box before you can trust it.  Call your banks and other institutions that can affect your credit rating for which you had data on this box.  After you've reformatted and reinstalled, you need to change every password yet again, using strong passwords that have nothing to do with your personal life.  This includes forum and email passwords.  Personally I use sections of an ssh key (not my authentication key) of around 15 to 20 characters.  Make several of whatever scheme you come up with, and don't use the same password for everything or even the same one for every example of one idea (bank accounts).

Install and correctly configure one or more utilities to detect intrusions.  Then pay attention to it and keep it up-to-date.  Start here:  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Get a full credit report in a couple months.  That is, if you stored anything that could possibly link you to a bank and give enough answers to security questions that they might be able to get past a banker.

Full disclosure:  I'm the network security guy at my company.  I regularly roast people for bad passwords and ... unwise ... practices.  That includes my boss and my wife.  There are definitely people around who know more about networking and computer security than I do, but IMO almost everyone I know is careless and/or lazy with this sort of thing.

---

### Post by grahammechanical on 2013-11-22
May I say something? This comment

> you would have to be root to see it all

Is one way of suggesting that we run the command with sudo in front of it.

It may not be the computer that is compromised but your Skype account or even the computer of your friend. Or the servers of the university. Does the university WiFi connection go through a server before going out to the telephone system.

Regards

---

### Post by dsurfer21 on 2013-11-22
> **1clue said:**
> 
As well, I'd make sure your ~/.ssh/authorized_keys* files are empty for that box too.  That's one way somebody could get in and do anything they want.




I tried: 
@D-ubuntu:~$ cat ~/.ssh/authorized_keys*
cat: /home/dsurfer21/.ssh/authorized_keys*: No such file or directory 


Does this mean that I don't have to worry about the authorized key issue?

---

### Post by dsurfer21 on 2013-11-22
> **grahammechanical said:**
> May I say something? This comment



Is one way of suggesting that we run the command with sudo in front of it.

It may not be the computer that is compromised but your Skype account or even the computer of your friend. Or the servers of the university. Does the university WiFi connection go through a server before going out to the telephone system.

Regards


This happened yesterday while using the MIT wifi network.  MIT definitely has servers. I'm guessing someone else like an MIT student saw my machine on the network and wanted to fool around.  I'm not sure how else to check to see where this person got access from.

---

### Post by 1clue on 2013-11-22
> **dsurfer21 said:**
> I tried: 
@D-ubuntu:~$ cat ~/.ssh/authorized_keys*
cat: /home/dsurfer21/.ssh/authorized_keys*: No such file or directory 


Does this mean that I don't have to worry about the authorized key issue?

Yes, not having it means you don't have to worry about it.

---

### Post by 1clue on 2013-11-22
How long were you using this system since you set up xrdp?

Certainly if somebody found an unauthenticated rdp server somewhere they would be tempted to mess around with it.  In fact I'm not even sure it qualifies as a wrongdoing at that point.  As an analogy, in some places (like where I live) if you leave your house open and somebody comes in and wanders around, they can't be charged with breaking and entering because there was no security in place.  It probably varies from place to place.

---

### Post by dsurfer21 on 2013-11-22
> **1clue said:**
> How long were you using this system since you set up xrdp?

Certainly if somebody found an unauthenticated rdp server somewhere they would be tempted to mess around with it.  In fact I'm not even sure it qualifies as a wrongdoing at that point.  As an analogy, in some places (like where I live) if you leave your house open and somebody comes in and wanders around, they can't be charged with breaking and entering because there was no security in place.  It probably varies from place to place.

I had set up that xrdp many months ago.  I haven't seen or noticed any issues until now.  I am only on the MIT wifi network every once in a blue moon, perhaps 3 or 4 times per year for a week each time.  The other times I am using my own wifi network in my house connected to my cable modem.  Nobody else uses this network except for me.   Occasionally I'll use it at a friends house.

In this instance, is it likely the person who intruded my system yesterday is someone also using the MIT network?

---

### Post by jamesisin on 2013-11-23
Is the MIT wireless network secured or is it an open network?

---

### Post by dsurfer21 on 2013-11-25
> **jamesisin said:**
> Is the MIT wireless network secured or is it an open network?

Sorry for the late response. It is a secured network.  You need to be an MIT affiliate or student, faculty, etc.  You need to register for an account to use the wifi.  Given that, is it likely someone was pranking me from within the MIT community?  I'm guessing this is most likely the case.  I don't think this person would have known me personally unless it was someone in the lab I was in at the time.

---

### Post by 1clue on 2013-11-25
You need to ask yourself how many different motives could be contained within the MIT network.  Keep in mind you have an unsecured service controlling a computer.  It could be argued that going in and trashing your system broke no laws.

---

### Post by bantuvez on 2013-11-26
I don't use desktop sharing so I don't know, but aren't remote connections logged in Ubuntu?

---

