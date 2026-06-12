---
title: "How to change themes in Xubuntu?"
date: 2007-08-31
forum: General Help
---

### Post by Stan_1936 on 2007-08-31
How do I install themes in XFCE?  Im using xubuntu and cannot change the theme in a straightforward way.  Infact ,I don;t know how to change the themes at all.  Google is giving me instructions for Ubuntu.

I found this on the forums:

cd /usr/share/themes/
sudo tar zxvf <theme_name>.tar.gz

Can someone please explain this to me?  I have downloaded my theme to my Home Folder...the filename is abc.tar.bz.  According to me my next step is 

```
cd /usr/share/themes/
```

then

```
sudo tar **[B][COLOR="Red"]zxvf[/COLOR]**[/B] <**abc**>.tar.gz
```

Can someone please explain to me what the text in red should be in my case?

---

### Post by bks on 2007-08-31
is the file a *.tar.bz or did you mean *.tar.gz?

---

### Post by Stan_1936 on 2007-08-31
Sorry, I meant tar.gz.  Am I correct and what is the significance of the text in red?

---

### Post by s26c.sayan on 2007-08-31
It really should be 
```
 tar [B]-zxvf 
```
[/B](Note the - before zxvf)

They are options for the tar command. 
E.g. z means filter the archive through gzip;
x means extract
v means use verbose mode
f means the filename follows

See **man tar** for details!

---

### Post by Stan_1936 on 2007-08-31
Thanks for the explanation, that really helps.  So would
```
sudo tar -zxvf <**abc**>.tar.gz
```
be correct for my case because I don;t have gzip and the theme itself is a .tar.gz format file, not a .zip format one?

---

### Post by bks on 2007-08-31
You don't have gzip? I thought it was standard on most, if not all, distros.

---

### Post by Stan_1936 on 2007-08-31
ok then I must have it....I meant I haven't specially downloaded it.  Sorry for the mix up.

---

### Post by Stan_1936 on 2007-08-31
Here's what I got:
```

turon@abcdefg:~$ cd /usr/share/themes/
turon@abcdefg:/usr/share/themes$ sudo tar -zxvf <abc>.tar.gz
bash: abc: No such file or directory
turon@abcdefg:/usr/share/themes$ 

```

Sorry, I' m a total newb so I'm a bit lost here...I downloaded it to the desktop before running those 2 commands above.

EDIT:  2nd attempt (also unsuccessful)

I extracted it to /home/username/.themes and used the Settings>User Interface  to try to select it, but it would not show up.  If it was not extracted to the proper location (/home/username/.themes) then where did it get extracted?

---

### Post by s26c.sayan on 2007-09-01
Why are you trying to untar <abc>.tar.gz!!!!!
Replace <abc> with the actual name of the file!

---

### Post by Stan_1936 on 2007-09-01
I renamed the file abc.tar.gz.

Guys, I'm almost ready to quit here...any help would really be useful to me.

---

### Post by kerry_s on 2007-09-01
unpack it were ever you have it, grab the folder and move it to .themes. you don't need root privileges. .themes folder you have to make, right click> create folder, .themes, it has to be a hidden folder so don't forget the "." dot in the front. press ctrl+h to see your hidden folders/files.
icons are done exactly the same way. 

then you just go menu> settings> settings manager and select what you installed.

i'll post pics in a bit, got to find a theme first. :)

---

### Post by Stan_1936 on 2007-09-01
Thank you.  However, how would I select icons?  I have inserted an icon folder into .themes.  Where do I select to use that icon set?

---

### Post by kerry_s on 2007-09-01
> **Stan_1936 said:**
> Thank you.  However, how would I select icons?  I have inserted an icon folder into .themes.  Where do I select to use that icon set?

my bag icons, go in .icons. you need to create that folder to.
then go settings> user interface> icon theme tab

so just create that folder and drag your icon folder from .themes to .icons. sorry, had to make the kids breakfast, so i rushed through that, should have been more clear.

you don't need pics again, do you?

---

### Post by Stan_1936 on 2007-09-01
Haha, thanks. you've been a great help.

No need for screenshots.

One last thing worth noting...I',m finding that I can only use themes that have a xwfm4 folder in them(once extracted).  Others simply do not show up in the Window Manager menu.  Is this expected?  

I just plucked a few from xfce-look...I really wanted the Mac theme(there is only 1) but it didn't work.  Do you know of any MacLook themes for Xfce?

---

### Post by kerry_s on 2007-09-01
> **Stan_1936 said:**
> Haha, thanks. you've been a great help.

No need for screenshots.

One last thing worth noting...I',m finding that I can only use themes that have a xwfm4 folder in them(once extracted).  Others simply do not show up in the Window Manager menu.  Is this expected?  

I just plucked a few from xfce-look...I really wanted the Mac theme(there is only 1) but it didn't work.  Do you know of any MacLook themes for Xfce?

yes, xfwm4 is for xfce, metacity is for gnome. the closes i can think of to mac is the spherecrystal, chances are you have it installed already, if not it's in the repo. see pic->
don't mind the missing pics, i didn't restart so there not there. second 1's after a quick logout and back in, mine you mines a custom install build up, so i don't have that many icons installed.

---

### Post by Stan_1936 on 2007-09-01
ok thanks, finally, is there any  install conky in Xfce?

Would this work?

```
   1.  $ sudo apt-get install conky
   2. $ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
   3. try running conky by typing "conky"! enjoy!

```

---

### Post by kerry_s on 2007-09-01
> **Stan_1936 said:**
> ok thanks, finally, is there any  install conky in Xfce?

Would this work?

```
   1.  $ sudo apt-get install conky
   2. $ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
   3. try running conky by typing "conky"! enjoy!

```

go for it! You want to> sudo apt-get install conky synaptic
synaptic makes it so much easier, to install, uninstall, search, etc...

---

### Post by Stan_1936 on 2007-09-01
ok, I've got a last question as they others have been answered.  I've attached a screenshot attached..how could I remove the window "surrounding conky" so as to just get the insides of it visible on my screen?

---

### Post by kerry_s on 2007-09-02
> **Stan_1936 said:**
> ok, I've got a last question as they others have been answered.  I've attached a screenshot attached..how could I remove the window "surrounding conky" so as to just get the insides of it visible on my screen?

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,skip_taskbar

```

you might also want to get rid of those icons>
mousepad ~/.config/xfce4/desktop/xfdesktoprc

```
[file-icons]
show-filesystem=false
show-home=false
show-trash=false
show-removable=true
```

---

### Post by Stan_1936 on 2007-09-02
Alright, worked and worked.

How do I remove the "Floppy Drive"(cause I don;t have a working floppy drive) and "51 G volume" icons from the desktop?

---

### Post by kerry_s on 2007-09-02
> **Stan_1936 said:**
> Alright, worked and worked.

How do I remove the "Floppy Drive"(cause I don;t have a working floppy drive) and "51 G volume" icons from the desktop?

for the floppy, just delete the folder from /media. 
the 51g volume, what is that?is it mounted?

normally what i would do is move it to /mnt, but you can't just drag & drop it.

first you need to have it unmounted, so> sudo umount /dev/?
look in fstab, your going to need to change that anyway> gksu mousepad /etc/fstab

so in fstab change the /media/? to /mnt/?
then move the folder from /media to /mnt> gksu thunar /media

---

