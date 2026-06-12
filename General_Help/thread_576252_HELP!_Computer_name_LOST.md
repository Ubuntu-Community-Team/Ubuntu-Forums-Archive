---
title: "HELP! Computer name LOST"
date: 2007-10-15
forum: General Help
---

### Post by Papa-san on 2007-10-15
In my usual ineptness with all things Linux, I managed to screw up my system.
I had a thread in Absolute beginners, but evidently didn't make my situation clear. 
As I was attempting to get my wireless re-configured, I guess I changed my systems name. When I used to open a terminal I would get this:```
john@ubuntu:~$
```
After messing with the wireless settings thrugh the networking GUI, my terminal gives me this:```
john@(none):~$
```

From terminal I cannot open any administartive programs. When I type ```
 john@(none):~$ sudo iwconfig 
<or any 'sudo' command> I get:
'sudo: unable to look up (none) by gethostbyname()'
```

I am also unable to open any GUI thet would require me to enter my password. So, I cannot get back into any GUI that would help me fix my issue in any way I can figure out. 
I have a LOT of work saved on that system, and many programs that took many days of headaches to get configured to work. I would REALLY prefer not to have to re-install everything. (For as much hell as it was, I'll prolly just re-install windows rather than re-do all that configuration.) There has to be a way to correct this, I imagine, but need someone who knows something about it to help.

My Ubuntu Box has been bulletproof until this point, and as my Ubuntu 6.06 is supposed to be LTS, I was hoping it truly is LTS! 8-[ Thanking you all in advance!

(I also think it might be a good idea to do something to keep this from being possible from networking... Might that be a bug thingy?)

---

### Post by bodhi.zazen on 2007-10-15
Boot to recover mode

Enter :

sudo hostname ubuntu

Or, to do it manually

nano /etc/hostname
nano /etc/hosts

In /etc/hosts you will have a line

127.0.0.1 localhost


Add in your hostname :


127.0.0.1 localhost ubuntu

Then re-boot ;)

[http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/](http://www.ducea.com/2006/08/07/how-to-change-the-hostname-of-a-linux-system/)

---

### Post by Papa-san on 2007-10-15
wonerful... Thanks.

Now... Questions from a dingbat:
1 - when I am in nano, I really don't know what to do.
 nano /etc/hostname opens a box that is empty except for the title and various commands at the bottom. (None of which I can actually get to do anything... what keys actually do things?)

nano /etc/hosts has text in the terminal window as you described. I see  my mistake as '127.0.0.1 localhost.localhost.myhome.net" is what should be changed to '127.0.0.1 localhost ubuntu'. I did that, but was unable to find any 'save' command, nor do I know what keystrokes I should use to save or exit while using nano.

2 - I have tried to get into my grub menu, but don't know how to do that either.

I really have a limited knowledge of how the inner workings of Linux do their things, but have learned a LOT so far! (I obviously, know just enough to be dangerous!) \\:D/

Thanks again!

EDIT: Aint that just like me? Didn't even notice there was a link for me. (Great info, but as yet unresolved...) I'll keep reading! LOL

---

### Post by bodhi.zazen on 2007-10-15
LOL

Sorry about that ...

You can navigate in the file with the arrow keys. You can type and delete/backspace.

To use the commands, use the control+ letter combination.

Ctrl+x to exit

It will ask if you want to save changes, type "Y" for yes ;)

If /etc/hostname is empty, that is the problem.

It should have a single line:> ubuntu

---

### Post by Papa-san on 2007-10-15
OK... I managed to get into GRUB. (The 'ESC' option shows up for approximately one second befor it boots past it.)

The first time it allows me to do anything, it is to enter the password, and it doesn't recognize it. My only known option is to press 'Ctrl-D', which boots me into the same unusable state.

However, in watchng it scroll, I think I saw why I am having wireless issues: Even though the last few times I have installed ubuntu, I have used channel 11 on my router, It seems to be loading information that tells it to connect to channel 6. My ESSID and WEP key show up right though...
So, once I get this fixed, I can begin tracking down why the channel insists on being wrong. I did post on this a while ago, but never got an answer as to where this information is saved so I can change it...

---

### Post by Papa-san on 2007-10-15
Sorry about the last post... I hadn't refreshed to see your post. 

Thanks. It makes sense. I tried it, though, and won't let me save in nano. It tells me 'permission denied'.

Evidently this is quite a quandry...

Might I do something with my live CD? I Hope SOMETHING works...!

---

### Post by bodhi.zazen on 2007-10-15
Yes, you could fix it with the live CD.

If you can not save it sounds like you are not in recovery mode, no problem, just sudo :

```
sudo nano /etc/hostname
```

Or if you prefer a gui :

```
gksu gedit /etc/hostname
```

HTH

---

### Post by Papa-san on 2007-10-15
I cannot get sudo priveleges in any environment I get into. Live or otherwise. I cannot sudo anything in any way for any reason... I have about a day until I just reformat her and install XP again...

One of the nicer things about windows is that when the OS does crap the bed, there is the option of installing the OS again without re-formatting the Hard Drive. I wish Ubuntuhad an option such as this. I really need all the other programs and all of the info on there, but the install I am running starts with"Which format option do you want to use?" What a pickle!

---

### Post by bodhi.zazen on 2007-10-15
well, that sounds off ...

From a live CD, open a terminal and :

```
sudo -i
```

You should now be root.

Also, if you are installing, why not re-install Ubuntu or dual boot ? You need to give yourself time to learn a new OS :twisted:

---

### Post by Papa-san on 2007-10-15
Well, that didn't even let me edit the files. I'll just re-install... It will take me a couple of weeks to get it back to where it needs to be, and that's the part that is so frustrating. The wireless that got me into this mess in the first place is the killer here. The Ubuntu operating system has some really bad quirks in regards to wireless with my particular box...

I make a lot of noise about going back to windows,but I doubt I will... :)
My laptop has been 100% Ubuntu for 2  years now. (I even have one of the "Powered by Ubuntu Linux" stickers where I peeled of my windows sticker... (I can't falsely advertise now, can I?) LOL

I do think I am going to do a dual boot, though. I'll keep the windows from accessing the internet, and I'll be able to use some of my games on the laptop.

So... I guess we can mark this problem as unresolved... (Bummer)

---

