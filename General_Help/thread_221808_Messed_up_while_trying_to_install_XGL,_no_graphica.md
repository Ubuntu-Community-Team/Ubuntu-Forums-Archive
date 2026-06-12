---
title: "Messed up while trying to install XGL, no graphical interface"
date: 2006-07-24
forum: General Help
---

### Post by Kevf on 2006-07-24
Yesterday I've tried to install XGL using the following two links:

[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)
[http://doc.gwos.org/index.php/Installxgl](http://doc.gwos.org/index.php/Installxgl)

I've used the first page starting at step two to install the components and used the second one to get xgl started. When I was finished, I didn't see any effects so I've tried the optional option at the bottom of the page of the second link:

[i]If compiz doesn't start with that method then just put this in the Sessions > Startup Programs 

LD_LIBRARY_PATH=/opt/mesa/lib /opt/fdo/bin/compiz --replace gconf decoration minimize move place resize rotate scale switcher wobbly zoom cube [/i]

I've just copy-pasted the command and rebooted (I'm still nog sure what the line beneath this command means:  *Categories: Dapper | Eye Candy*  :-k )

Now Linux isn't able to boot X (graphical interface) and the only thing I've got access to is the terminal ](*,) 

I think this is because I've added the last commandline, but I haven't got any clues how to put things back the way they were.

Could someone please tell me step by step what to do? I'm at work now, so the only option for me is to make a print and take it back home :mrgreen: 

Next time I'll be more patient when the forum is down and will use the beautiful sticky at the top of this subforum :rolleyes: 

Thanks in advance

Kevin

---

### Post by cloud8421 on 2006-07-24
Try this (goes back with your old gdm configuration):
```

sudo mv /etc/gdm/gdm.conf-custom~ /etc/gdm/gdm.conf-custom

```
Then try to remove the .Xsession file (we'll simply move it):
```

mv .Xsession .Xsession-back

```

As far as I can see the last command is simply an environment variable (may be I'm wrong), so it shouldn't be connected with your problem.

---

### Post by gmatt on 2006-07-24
As cloud said just remove the Xsession file and everything should go back to normal. I'd even recommend rm ~/.Xsession if you want.

---

### Post by Kevf on 2006-07-24
But don't I need xsession for any further use? 
the firts option just cleans it, right?

---

### Post by gmatt on 2006-07-24
To my understanding the ~/.Xsession file is used only optionally to specify any changes you want to make to the Xsession you want to run. If you delete it, everything will go back to the default gdm settings.

---

### Post by gmatt on 2006-07-24
I'm not sure what cloud means by 

sudo mv /etc/gdm/gdm.conf-custom~ /etc/gdm/gdm.conf-custom

because the guide you used to setup your XGL did not instruct you to edit your gdm.conf file. The guide you used to setup XGL attempts to use the ~/.Xsession file to accomplish the same objective. Simply deleting the ~/.Xsession file should fix you up :) Before you do that though, post its contents and I'll tell you if you have anything really iportant in there.

---

### Post by Kevf on 2006-07-24
xsessions was empty before editting it

damn maybe I should have posted this in the newbie section:
how can I see the contents of xsession by using the terminal?

gedit .xession  ?

---

### Post by cloud8421 on 2006-07-24
The second link told Kevf to modify gdm.conf-custom, but I don't know if he did. If he didn't, then the command i told him to execute simply won't work, without harming the system.

To see what's inside .Xsession you can type
```

gedit .Xsession

```
as you said (but you need X server to work), or
```

cat .Xsession

```
to read the file or
```

vim .Xsession

```
to edit the file, but you need to know how to use vim (a little).

---

### Post by Kevf on 2006-07-24
Whoohoo! Back again: both of you, tnx a lot!

I'll try this link instead

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)


:mrgreen:

---

### Post by Beamerboy on 2006-07-24
> **Kevf said:**
> Whoohoo! Back again: both of you, tnx a lot!

I'll try this link instead

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)


:mrgreen:

I just wrote an updated HOWTO today which you can find here:

[http://www.ubuntuforums.org/showthread.php?t=222034](http://www.ubuntuforums.org/showthread.php?t=222034)

Beamerboy

---

### Post by Kevf on 2006-07-25
Ok last chance for Linux. I've used the Howto in the link I've mentioned above and run in to another big problem ](*,) 

Ubuntu stops at a a grey screen (the brown screen where the inlog used to pop up) and the waiting-circle just keeps spinning. 
Does anybody kwows how to fix this problem? 
:confused: 

@ Beamerboy:  Your how to is the last chance. :-D

---

### Post by Kevf on 2006-07-26
Bump..... still stuck at the grey screen :neutral:

---

### Post by Kevf on 2006-07-26
bump, getting a little frustrated....still nothing works, even borrowed a laptop to do some internetting and looking for sollutions :-(

---

### Post by John.Michael.Kane on 2006-07-26
Kevf when asking for help please include your system spec's. no one knows what your trying to run xgl/compiz on. 32/64 bit ubuntu what videocard maker.

---

### Post by Kevf on 2006-07-27
Hmm ok no prob,since I didn't post it the first time, I thought it was no prob.

Specs:
Barebone Asus Pundit
2,6 Ghz pentium processor
512 mb Ram

Ati Radeon Express 200 chipset

I believe I'm using the 686 kernel now. I hope this is sufficient. :D

---

### Post by Kevf on 2006-07-28
I'm getting a little frustrated over here. I still haven't found a solution and my girlfriend wants her laptop back ;) 

There are too many important files on my hd to do a clean install, so I would really appreciate some help :D

---

### Post by gmatt on 2006-07-28
From the howto that you used which method did you pick the "normal" howto or the other howto. I think the best way to go back to the normal settings that you had before is to revert them manually. So here goes. I assume you only have a terminal available to you so here is one way to fix it assuming you used the normal howto. 

```
sudo nano /etc/gdm/gdm.conf-custom 
```

change
```
[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 
```

to 
```
 [servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). [COLOR="Red"]
# [/COLOR]1=Xgl 
```

All you are doing is commenting out code that changed your X server around. This is a useful technique in many things such as programming and various other config file mixups. 

editing with nano is fairly intuitive. To search for text use Ctrl+W and to save or write to file use Ctrl+O. To quit use Ctrl+X.

 then

```
sudo nano /etc/gdm/gdm.conf 
```
change back to 

```

0=Standard
#1=Standard
```

Same concept as above

```

GdmXserverTimeout=10

```

Then save everything and to start up your xserver/gnome session again all you have to do is 

```

sudo gdm

```

---

### Post by gmatt on 2006-07-28
Also, I think one reason why you might not be able to run XGL is because you do not have the ati drivers (FGLRX) properly installed/enabled so that you go not have 3D acceleration. One easy way to find out is:

```

glxinfo | grep direct
direct rendering: [color=green]Yes[/color]

``` 

If you get the above message then you are fine. But if you get the message

```

glxinfo | grep direct
direct rendering: [color=red]No[/color]

```

Then you need to install the proprietory ATI graphics drivers. There are a lot of Howtos on how to do that, on these forums and on google.

---

### Post by Kevf on 2006-07-29
Thanks for the help! I only needed the first step to get back in:D

Edit: direct rendering is on no, just as you suspected..... I've got a lot of work to catch up to, but I'm going to give it a new try tomorrow :D

---

