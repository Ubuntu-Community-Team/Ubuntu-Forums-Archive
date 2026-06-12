---
title: "Trouble synching treo 650 on Fiesty Bluetooth Problem"
date: 2007-05-16
forum: General Help
---

### Post by wormeyman on 2007-05-16
[http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

So that guide worked for me on edgy and since i was having problems on fiesty i decided to re-follow the guide ti figure out what wasn't working.  On fiesty i can see my treo using hcitool scan but i cannot connect when i reach this step

Create new network
>Prefs
>Network
>Menu > Service > New
>Enter a Name
>Enter Connection, don't set username or password
>Select details > Idle timeout to 3 mins.
>Ok
>Connect **This is where it falls apart**

I also tried using [http://www.belutz.net/2007/05/14/pairing-bluetooth-devices/](http://www.belutz.net/2007/05/14/pairing-bluetooth-devices/) but that didn't help either.

---

### Post by tgm4883 on 2007-05-16
hmm, thats the same guide i followed to get my 650 to sync with feisty via bluetooth.

Trying to remember what I did to get it to work as i remember it wasn't exactly following the guide to the letter.

Do you have these installed?

```
bluez-gnome
bluez-pin
bluez-utils
```

Do you have the bluetooth applet in the corner of your screen?  I seem to remember being stuck at the part where I had to type the pin in to make a connection between the two.  It wouldn't work until I had the bluetooth applet up there.

---

### Post by Rescue9 on 2007-05-23
I'm having the same problem. Every time I try to connect in the network section of my Treo, I get the 0x0305 error. 

I've tried 4 or 5 different howto's and all lead to the same thing. Hotsync with USB works great, but not with bluetooth. And yes... I do have the files listed above.

---

### Post by Rescue9 on 2007-05-24
WOOOHOOOO!!!!! I got it to work and it syncs with Evolution via Bluetooth!!!!

THe problem was the line

```
sudo /etc/init.d/bluetooth restart
```

For some reason restart[ing] the connection didn't work. HOWEVER< if you stop then start the connection after a few seconds it works like a charm!

Keep following the instructions as provided.

---

### Post by wormeyman on 2007-05-26
I'm still having trouble connecting my pc can see my phone via

```
hcitool scan
```

I also get the 0x0305 error

I also changed my /etc/bluetooth/hcid.conf to change my password and still no luck.

---

### Post by wormeyman on 2007-06-01
bump for some more ideas :(

---

### Post by Rescue9 on 2007-06-03
Saw the bump... :-P 

The only 2 reasons I found for a 0x0305 error are this:

1. bluetooth isn't turned on prior to trying to connect
2. you issued a ```
sudo /etc/init.d/bluetooth restart
``` command instead of ```
sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/bluetooth start
```

Those are the only 2 reasons I found while searching the web for myself.

---

### Post by wormeyman on 2007-06-03
I'm starting to wonder if the problem is on my phones end however it did work when i used edgy?

---

### Post by digitalbenji on 2007-06-04
this simply did not work for me.  I'd like to set up DUN, and I have the username/password needed for the cingular network (my carrier), can someone guide me through this?

---

### Post by byunique on 2007-06-04
I just posted my complete write up... the login information is there...

[http://ubuntuforums.org/showthread.php?t=464613](http://ubuntuforums.org/showthread.php?t=464613)

---

### Post by YaroMan86 on 2008-04-28
Bumping this thread. I have a Treo 650. Did the stupid stop, start thing as mentioned earlier in this thread, and I am still getting a 0x0305 error.

---

### Post by tgm4883 on 2008-04-28
> **YaroMan86 said:**
> Bumping this thread. I have a Treo 650. Did the stupid stop, start thing as mentioned earlier in this thread, and I am still getting a 0x0305 error.

Check the bad modem fix on my webpage.  I tested it in hardy, but believe that it will work on previous distros.

:EDIT:

I should add the link [http://linux.weilandhomes.com/treo650](http://linux.weilandhomes.com/treo650)

---

