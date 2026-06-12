---
title: "[SOLVED] Set Resolution in Terminal"
date: 2007-11-04
forum: General Help
---

### Post by AsoSako on 2007-11-04
One of my monitors just died which was at 1280x1024 and 63 refresh rate.  I put my other one which does not support this resolution and refresh rate but support 1024x768 @ 60 Hz.  Now I need to set its resolution and refresh rate from the login terminal through Ctrl+Alt+F3 but I don't know how...  If you know how to or if there is any other way to get my monitor to work please tell me

---

### Post by taurus on 2007-11-04
You just edit /etc/X11/xorg.conf and change it to the right one.

```
sudo nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.

---

### Post by AsoSako on 2007-11-04
Ok...  Sorry I am a little new to this.  So I get to the xorg.conf and how do I proceed from there?  What exactly do I have to write there?

---

### Post by ryanVickers on 2007-11-04
there should be a section on certain resolutions, colour depths, and refresh ratess - just change them all to be sure ;)

---

### Post by AsoSako on 2007-11-04
How do I get to those sections?  All I get after I type this command is a Black screen saying that I am in this nano thing and some hotkeys at the bottom...

---

### Post by taurus on 2007-11-04
> **agsimeonov said:**
> How do I get to those sections?  All I get after I type this command is a Black screen saying that I am in this nano thing and some hotkeys at the bottom...

Can you post the _exact_ command that you typed at a prompt?

---

### Post by Denn1s on 2007-11-04
i think its a little extremist, but you can try to reconfigure x
```

sudo dpkg-reconfigure xserver-xorg

```
it will ask you some questions about keyboard and about your monitor, try to bacup xorg.conf first if you can
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bacup

```

---

### Post by AsoSako on 2007-11-04
> **taurus said:**
> Can you post the _exact_ command that you typed at a prompt?

sudo nano -Bw /etc/X11/xorg.conf 

The command you told me to type...

How do I proceed from there?

---

### Post by taurus on 2007-11-04
What's the output of this command from a terminal?

```
ls -la /etc/X11
```

---

### Post by AsoSako on 2007-11-04
It is way to long and I can't copy paste it since I have to boot up on my Windows XP partition in order to respond... :(
Anyhow I have no trouble entering the xorg with sudo nano -Bw /etc/X11/xorg.conf I just don't know how to get to editing it...

---

### Post by AsoSako on 2007-11-04
Never mind.  I forgot that the terminal was case sensitive and I was mistyping it.  I figured it out.  Thanks for all the help.

I just have one more question.  Is installing BulletProof-X a good idea?  Will it help in situations like this?

---

