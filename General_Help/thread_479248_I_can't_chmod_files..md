---
title: "I can't chmod files."
date: 2007-06-20
forum: General Help
---

### Post by phizikal on 2007-06-20
Ok, I wanted to download the Ubuntu Studio theme, well I had to edit a file.

Well, i did it and it wont let me save. It says the file is read and writeable. But i tried editing it manually, and i get an error saying im not the owner. Which i am.

Anyone can help me with this? Please and thank you's.

---

### Post by Ayuthia on 2007-06-20
Where is the location of the file?  If it is located in someplace like /etc/X11, you would need to edit as root (sudo/gksu).

---

### Post by phizikal on 2007-06-20
It's located in -  /etc/apt/sources.list

It saids I don't have permissions, which I am the owner of this system.
I tried using terminal to set the cmhod settings, but no.. =/

---

### Post by Ayuthia on 2007-06-20
This is one of those files that you would need root privileges.  You would need to use 

gksu gedit /etc/apt/sources.list

to update.

---

### Post by phizikal on 2007-06-20
this is what i got.


```
(gedit:28059): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

```

---

### Post by Ayuthia on 2007-06-20
ok...I expected the authentication rejected part, but the rest is new to me.

Let me take a step back.  How do you normally edit a file?  Do you use gedit?

---

### Post by phizikal on 2007-06-20
Yes I do.

It's also not letting me put files into my var/www file either.

is there something i have misconfigured thats letting not have my permissions?

---

### Post by Ayuthia on 2007-06-20
Another option for now would be to copy the file to your home directory and then do:

sudo cp $HOME/sources.list /etc/apt/sources.list

I normally do my editing via the vi editor, but I generally don't tell others to use it because if you never have used it, it can be very cryptic.

---

### Post by Ayuthia on 2007-06-20
> **phizikal said:**
> Yes I do.

It's also not letting me put files into my var/www file either.

is there something i have misconfigured thats letting not have my permissions?

No.  The items that you have been trying to modify are in places where the system only wants root to update.  It is to protect the system from letting a normal user go and modify the file.

If you want to copy a file into /var/www, you would need to do 'sudo cp <file> <destination>'

I am not for sure why you are not able to get into gedit by using the command at the terminal.  Normally, this should not trigger the sound card.

---

### Post by Ayuthia on 2007-06-20
> **phizikal said:**
> this is what i got.


```
(gedit:28059): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

```

Did gedit come up when you entered the command?  I am wondering if the ALSA messages came up for another reason.

---

### Post by phizikal on 2007-06-20
Yes it did.

---

### Post by Ayuthia on 2007-06-20
One other option for adding a line to /etc/apt/sources.list is the following:

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list

You would need to replace the quoted item with the one that you are trying to add.  The option that I listed above came from the medibuntu Repository HowTo.

---

### Post by Ayuthia on 2007-06-20
> **phizikal said:**
> Yes it did.

If you did, you should be able to modify and save the file.  I am guessing that the ALSA messages appeared for another reason.  Sometimes the system will post messages to the terminal when something happens and this might have been a coincidence where you typed something and the message appeared right after.

I was wrong about the ALSA messages being coincidental.  I did a search and found someone else that has the same issue.  It does not appear to hurt anything, but I have found a solution for that problem.

---

