---
title: "Noble Numbat : How to add bark alert sound ?"
date: 2024-09-07
forum: General Help
---

### Post by georgesgiralt on 2024-09-07
Hello Guys,
I'm fanatic about the barking sound on alert. I _do_ love it. 
And I was very disappointed upon upgrading from 22.04 LTS to 24.04.1 LTS to see the sound was missing. 
I copied it from a computer still in 22.04 to /usr/share/sounds/gnome/default/alerts/bark.ogg :
```
$ ll /usr/share/sounds/gnome/default/alerts
total 100
-rw-r--r-- 1 root root 13322 sept.  7 17:18 bark.ogg
-rw-r--r-- 1 root root 10510 mars  27 14:50 click.ogg
-rw-r--r-- 1 root root 39834 mars  27 14:50 hum.ogg
-rw-r--r-- 1 root root 18245 mars  27 14:50 string.ogg
-rw-r--r-- 1 root root 11445 mars  27 14:50 swing.ogg
$
``` 
But it does not show in the "Alert sound" drop down menu in Preferences/Sound ???
Even after a reboot.
So I would like to know how to add this "iconic" alert sound to my Noble Numbat laptop ? 
Manu thanks in advance for your help ! 
Have a nice day !

---

### Post by 1fallen on 2024-09-07
They removed it 2 years ago: [https://gitlab.gnome.org/GNOME/gnome-control-center/-/merge_requests/1293](https://gitlab.gnome.org/GNOME/gnome-control-center/-/merge_requests/1293)

---

### Post by georgesgiralt on 2024-09-07
Yes, but how to add it back ?

---

### Post by 1fallen on 2024-09-07
Revert back to 22.04. 
They have no plans to add it back...

I guess you could complain or request it be brought back...But we all know how that goes over with the Gnome Boys.

---

### Post by georgesgiralt on 2024-09-07
Well I did put it in the folder where the alert sounds are stored, but it is not showing in the drop down menu... 

[IMG]https://i19.servimg.com/u/f19/17/79/70/72/captur48.png[/IMG]

So what to do to update the drop down menu to reflect the content of the folder the sounds are stored in ?

---

### Post by 1fallen on 2024-09-07
I can't word it any better:
> 
[LIST]
[*][Georges Basile Stavracas Neto]("https://gitlab.gnome.org/feaneron")[[COLOR=#9E9689]@feaneron[/COLOR]]("https://gitlab.gnome.org/feaneron")[COLOR=#9E9689]· [2 years ago]("https://gitlab.gnome.org/GNOME/gnome-control-center/-/merge_requests/1293#note_1438000")[/COLOR]
[COLOR=#9E9689][CENTER]Developer[/CENTER]
[/COLOR]

GNOME is not on the dog barking sounds business anymore
[*]
[LIST]
[*]
[/LIST]





 
[/LIST]


---

### Post by georgesgiralt on 2024-09-07
OK. 
Suppose I want to add a sound like a pig cry? How do I do that ? IT is not barking ;-)

---

### Post by 1fallen on 2024-09-07
I'm speaking with a friend now, and he's not sure but has indicated possibility....so will you show me this Please:
```
ls /usr/share/sounds/gnome/default/alerts/
```

---

### Post by georgesgiralt on 2024-09-07
But of course :
```
$ ls /usr/share/sounds/gnome/default/alerts/ 
bark.ogg  click.ogg  hum.ogg  string.ogg  swing.ogg
$
```
And this is alerady shown in first post of this thread.

---

### Post by 1fallen on 2024-09-07
So you did :P
Now we need to see this, to make sure it is in here:
```
cat /usr/share/gnome-control-center/sounds/gnome-sounds-default.xml
```

---

### Post by Dennis N on 2024-09-07
In some Gnome applications like Gnome Clocks you no longer can switch the sound file. I used to substitute my own alarm sound for the default "alarm-clock-elapsed" by redirecting with a symbolic link. That is now ignored. The sound file might be complied with the program itself? My solution was to switch to a different alarm clock/timer that allows customizing.

The sound files for "Clocks" were here: /usr/share/sounds/freedesktop/stereo

---

### Post by georgesgiralt on 2024-09-07
No joy here :
```

$ export LANG=C
$ cat /usr/share/gnome-control-center/sounds/gnome-sounds-default.xml 
cat: /usr/share/gnome-control-center/sounds/gnome-sounds-default.xml: No such file or directory
$ 

```

---

### Post by 1fallen on 2024-09-07
> **georgesgiralt said:**
> No joy here :
```

$ export LANG=C
$ cat /usr/share/gnome-control-center/sounds/gnome-sounds-default.xml 
cat: /usr/share/gnome-control-center/sounds/gnome-sounds-default.xml: No such file or directory
$ 

```
I'm just not a Gnome user so you will have to bare with me on this:
What's in here:
```
ls [COLOR=#E8E6E3][FONT=&quot]/usr/share/gnome-control-center/sounds[/FONT][/COLOR]
```

---

### Post by georgesgiralt on 2024-09-07
Ls where ? In my home directory ? Because this one is HUGE ....

---

### Post by georgesgiralt on 2024-09-07
Sorry. I'm tired from old age ;-) 
```

$ ll /usr/share/gnome-control-center/sounds/ 
ls: cannot access '/usr/share/gnome-control-center/sounds/': No such file or directory
$ ll /usr/share/gnome-control-center         
total 16
drwxr-xr-x 2 root root 4096 Sep  3 16:43 default-apps
drwxr-xr-x 3 root root 4096 Oct 17  2019 icons
drwxr-xr-x 2 root root 4096 Sep  3 19:33 keybindings
drwxr-xr-x 2 root root 4096 Sep  3 19:22 pixmaps
$ 

```

P.S. : Same output on a laptop running 22.04 LTS ... 
Enjoy ;-)

---

### Post by 1fallen on 2024-09-07
This seems like a lot of work for just a sound, but I'll hang in there with you for a bit more.


Open the Files (Nautilus) application and head over to /usr/share/sounds/gnome/default/alerts. You will find a folder containing the files used as the default alert sounds in Ubuntu. Copy them to a separate folder on your PC.


Next, choose a new alert sound. You can use a sound from a personal file or download an interesting audio clip from a sound database website. Save the file to your computer and then use an online audio converter to convert your sound clip into an OGG file.
Or, Just rename an exsisting file with your bark.ogg


But after moving the sound files you will have to copy it back:
```
sudo mv bark.ogg /usr/share/sounds/gnome/default/alerts
```
But change it to one of the already shown options:
```
click.ogg
hum.ogg
string.ogg
swing.ogg
```

---

### Post by Dennis N on 2024-09-07
I tested this out for the alert sound. You can just make a symbolic link from an existing alert to your file.

```
dmn@tyana:/usr/share/sounds/gnome/default/alerts$ ls -l
total 96
-rw-r--r-- 1 root root 10510 Mar 27 06:50 click.ogg
-rw-r--r-- 1 root root 12182 Sep  7 11:03 [COLOR="#FF0000"]dialog-error.oga[/COLOR]
-rw-r--r-- 1 root root 39834 Mar 27 06:50 hum.ogg
-rw-r--r-- 1 root root 18245 Mar 27 06:50 old-string.ogg
lrwxrwxrwx 1 root root    16 Sep  7 11:12 [COLOR="#FF0000"]string.ogg -> dialog-error.oga[/COLOR]
-rw-r--r-- 1 root root 11445 Mar 27 06:50 swing.ogg

```

I added a new sound file to the alerts folder - **dialog-error.oga** 
I moved **string ogg** to **old-string.ogg** 
I made a symbolic link: **sudo ln -s dialog-error.oga string.ogg**
So, when I choose **string** as the alert, it actually plays **dialog-error**.

---

### Post by georgesgiralt on 2024-09-07
Sorry. I'm tired from old age ;-) 
```

$ ll /usr/share/gnome-control-center/sounds/ 
ls: cannot access '/usr/share/gnome-control-center/sounds/': No such file or directory
$ ll /usr/share/gnome-control-center         
total 16
drwxr-xr-x 2 root root 4096 Sep  3 16:43 default-apps
drwxr-xr-x 3 root root 4096 Oct 17  2019 icons
drwxr-xr-x 2 root root 4096 Sep  3 19:33 keybindings
drwxr-xr-x 2 root root 4096 Sep  3 19:22 pixmaps
$ 

```
Enjoy ;-)

---

### Post by georgesgiralt on 2024-09-07
Humm, my new post did not show but the old one did. 
I'll reply tomorrow when the brain will be fresh from sleeping...

---

### Post by georgesgiralt on 2024-09-08
Hello Guys,
You gave workaround which, obviously, work. Either linking the "proper sound" to a "sanctioned" sound or replacing one. 
Actually, this is not my question. 
I would like to learn and know. Did this all my life.
I'm very surprised that Gnome use, obviously, a complex method to produce the pop-up list of sounds to select. I was (wrongly) thinking that the list was dynamically constructed by reading the content of the directory for alert sounds. 
This is not the case. 
So, where are the pop-up lists constructed and how ? This is my question exactly. And how could I custom tweak them ? 
I need to find this because the problem will show upon update of Gnome packages and/or Ubuntu upgrades... 
Thanks a lot for your help and advices ! 
Have a nice and bright day !


P.S. : Noble Numbat alert sounds are not IMHO alert sound. Gentle click or smooth sound do not alert me of a potential un-secure situation.  Barking does. When my laptop bark at me, I _know_ I've done something wrong..... Of course your mileage may vary and opinions differ from mine, I've no problem with that.  But I would consider addition of more "alerting" sounds a plus by the Gnome team. And let the choice of level of alerting to the user.

---

### Post by georgesgiralt on 2024-09-08
It's me again. 
I forgot to say that Google was my friend, yesterday. 
I've found another way to set the sound I need. And this darken the plot somewhat. It involves Pulse Audio : 
```
 pactl upload-sample /usr/share/sounds/gnome/default/alerts/bark.ogg bell-window-system 
```
Of course, this command worked perfectly...

---

### Post by Dennis N on 2024-09-08
The alert sound is best described as "this action isn't possible". Not that its dangerous, something wrong with the system, or something insecure.
The 5 choices in the alert sound list are likely determined in the source code or an un-editable gresource file and can't be edited by the end user.

---

