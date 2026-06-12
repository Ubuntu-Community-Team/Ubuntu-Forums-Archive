---
title: "my system fall cant go to the log in screen"
date: 2008-03-09
forum: General Help
---

### Post by Turge on 2008-03-09
Hello !
I have try to installed Ati radeon driver on my ubunti linux 7.10.
like in the tutorials they gave me here :
[http://ubuntuforums.org/showthread.php?t=718983]("http://ubuntuforums.org/showthread.php?t=718983")
and i have installed it in the manual way in the secound time cuz i wansen't sure if it's installed and i asked and nobody answer so i just try in the manual way.

and they said there to make restart after and now when i restart the system i cant go to the log in screen.
it's say's "problem in the 'X' server to see the problem press yes" or something like that.
so i press yes and it's said" faild GDM Driver configure the GDM driver and than reboot again and log in" or something like that.
so i can't go in to the linux and i'm in a real problem.
so i tryed to make a reapir to my system it's ask me when i reboot  wich OS I want to use so i have a reapir way there. so i press that and it's doesen't fix the problem.

but after it's say's me on the start all the error with the GDM driver it's take me to a black screen like a terminal realy like a terminal and it's say's put the user name and then it's say's to put the password so i put but it's donsen't help i can only use the terminal now.

so what i should to do?
I dont have a ubuntu linux now :( 
somebody can help me please?


just u to know i have ubuntu linux 7.10

Thank you for every answer.

---

### Post by justsomedude on 2008-03-09
Ok, no reason to panic. :)

Did the installation go well?

If yes, boot and login. Like you have done before (remember, the black thing that looks like a terminal? it actually is a terminal)

Then do:

```
sudo aticonfig --initial
```
 

(you will have to enter your password again) and then 

```
sudo aticonfig --overlay-type=Xv
```

and then reboot.

```
sudo reboot
```



If that doesn't work, don't worry, we'll get this sorted out...

---

### Post by Turge on 2008-03-10
the instalation of the ubuntu linux was very good.
and it's work 2 weeks very good the linux the problem starts when i try to install the ati radeon driver and then i reboot than the problem starts.

[B]So i think now i realy need to by worry because it's says to me :
Sudo : aticonfig:command not found[/B]

What i should to do now please someone will help me!

---

### Post by Turge on 2008-03-10
> **Turge said:**
> the instalation of the ubuntu linux was very good.
and it's work 2 weeks very good the linux the problem starts when i try to install the ati radeon driver and then i reboot than the problem starts.

[B]So i think now i realy need to by worry because it's says to me :
Sudo : aticonfig:command not found[/B]

What i should to do now please someone will help me!

anyone knows how to fix that problem????

---

### Post by justsomedude on 2008-03-10
Ok, what I wanted to know was if the ati driver installed properly. Obviously it didn't, otherwise the commands above would have worked.

So what you have to do know is, boot, and then login as you have done before.

Then do:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

(enter your password again) 

And then:

```
sudo dpkg-reconfigure xserver-xorg
```

Remember that the command prompt is case sensitive, so write this carefully.

The system will then ask you various questions about your hardware. Read the instructions carefully and answer everything to the best of your knowledge.

Now, when your are prompted to choose the video driver, choose "vesa".

When you're done, reboot and you will have a graphical environment again. Then we can take care of the rest. :)

---

### Post by Turge on 2008-03-10
> **justsomedude said:**
> Ok, what I wanted to know was if the ati driver installed properly. Obviously it didn't, otherwise the commands above would have worked.

So what you have to do know is, boot, and then login as you have done before.

Then do:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

(enter your password again) 

And then:

```
sudo dpkg-reconfigure xserver-xorg
```

Remember that the command prompt is case sensitive, so write this carefully.

The system will then ask you various questions about your hardware. Read the instructions carefully and answer everything to the best of your knowledge.

Now, when your are prompted to choose the video driver, choose "vesa".

When you're done, reboot and you will have a graphical environment again. Then we can take care of the rest. :)
thank you for all but my brother fix that before ur message.
he print the  " HOW TO INSTTAL ATI RADEON DRIVER"
so he print that.
and he looks on that and put some code and now it's works but i still dont have a ati radeon driver and i'm afraid to touch it cuz if i touch it it's can broke again.

so if u have a new tutorials how to install the ati radeon driver that work for sure and dont broke my computer like the guy that gave it to me before  i will by happy.

thx.

---

