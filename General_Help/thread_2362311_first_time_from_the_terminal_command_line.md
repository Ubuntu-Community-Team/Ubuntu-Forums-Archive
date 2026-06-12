---
title: "first time from the terminal command line"
date: 2017-05-26
forum: General Help
---

### Post by xpeaceservant on 2017-05-26
So I'm attempting to load "Mystic BBS" software onto Ubuntu. I downloaded the Linux version.  I cheated and made a directory from another place in Ubuntu.  Here are the instructions I was given to load up the software:
```
sudo chown myusername:myusergroup /mystic 

    ./install
```

What I actually typed and the error response is below.  First I asked what my user group was because I had no idea. Turns out I'm the admin, or adm. 
```
david@SHIRAZ:/media/david/6ED0C5CAD0C5992B/MYSTIC$ groups david
david : david adm cdrom sudo dip plugdev lpadmin sambashare
david@SHIRAZ:/media/david/6ED0C5CAD0C5992B/MYSTIC$ sudo chown david:admin /mystic./install
chown: invalid group: &#8216;david:admin&#8217;
david@SHIRAZ:/media/david/6ED0C5CAD0C5992B/MYSTIC$ sudo chown david:adm /mystic./install
chown: cannot access '/mystic./install': No such file or directory
david@SHIRAZ:/media/david/6ED0C5CAD0C5992B/MYSTIC$ sudo chown david:adm /mystic ./install
chown: cannot access './install': No such file or directory
```

Best I can tell I am not supposed to word wrap it as it appears above. And I don't know how to do that anyway. I typed what I thought I should but it says 'no such directory'.  One time I typed 'mystic./install' and another I separated them a bit with 'mystic ./install'.

How far off am I in being literal here?

Cheers!

---

### Post by deadflowr on 2017-05-26
adm is not what you think it is.
it's the group for users to be able to read log files.
the admin group is sudo.
fyi

---

### Post by steeldriver on 2017-05-26
... also, they are two separate commands

```

sudo chown myusername:myusergroup /mystic

./install

```

NOT

```

sudo chown myusername:myusergroup /mystic./install

```

---

### Post by xpeaceservant on 2017-05-27
My group or admin group? Or are they the same thing?  When I had used 'adm' I noticed it didn't give me a hey dummy error.

---

### Post by xpeaceservant on 2017-05-27
> **steeldriver said:**
> ... also, they are two separate commands

```

sudo chown myusername:myusergroup /mystic

./install

```



Ah, that makes sense. Two distinct commands. Thank you.

---

### Post by xpeaceservant on 2017-05-30
I thought it was solved. Not so.  Here is a screen shot of what's happening.
[ATTACH=CONFIG]275360[/ATTACH]
I am trying to install the Mystic program.  Suggestions, please.

---

### Post by SeijiSensei on 2017-05-30
You need to set the execute bit on the program:
```

cd ~/MYSTIC
chmod a+x install

```
If chmod throws a permissions error, use "sudo chmod a+x install".

---

### Post by deadflowr on 2017-05-30
It's probably because the file isn't set as executable
try making it executable by running
```
chmod +x install
```
then try running the ./install command again.

ninja'd

---

### Post by vasa1 on 2017-05-31
> **xpeaceservant said:**
> I thought it was solved. Not so.  Here is a screen shot of what's happening.
[ATTACH=CONFIG]275360[/ATTACH]
I am trying to install the Mystic program.  Suggestions, please.
Side issue: you can copy/paste information from the terminal rather than take a screenshot. Copy/paste will work even when you have more than one screen of information :)

---

### Post by xpeaceservant on 2017-05-31
Oh, ok. Well, I'm new here too. Ha!  I'll try to remember that.

---

### Post by xpeaceservant on 2017-05-31
> **SeijiSensei said:**
> You need to set the execute bit on the program:
```

cd ~/MYSTIC
chmod a+x install

```
If chmod throws a permissions error, use "sudo chmod a+x install".

Hmm...
I tried this ...
david@SHIRAZ:~/MYSTIC$ cd ~/MYSTIC
david@SHIRAZ:~/MYSTIC$ chmod a+x install
david@SHIRAZ:~/MYSTIC$ sudo chmod a+x install
[sudo] password for david: 
david@SHIRAZ:~/MYSTIC$ 

I keep feeling like there is something intuitive I'm missing here.  Kind of like being asked to find butter in a refrigerator full of butter and not seeing it.  :p

[by the way, that cut and past thingy from the Terminal was great]

---

### Post by deadflowr on 2017-05-31
> **xpeaceservant said:**
> Hmm...
I tried this ...
david@SHIRAZ:~/MYSTIC$ cd ~/MYSTIC
david@SHIRAZ:~/MYSTIC$ chmod a+x install
david@SHIRAZ:~/MYSTIC$ sudo chmod a+x install
[sudo] password for david: 
david@SHIRAZ:~/MYSTIC$ 

I keep feeling like there is something intuitive I'm missing here.  Kind of like being asked to find butter in a refrigerator full of butter and not seeing it.  :p

[by the way, that cut and past thingy from the Terminal was great]

What happens when you launch the ./install command now?

---

### Post by vasa1 on 2017-05-31
> **xpeaceservant said:**
> Hmm...
I tried this ...
david@SHIRAZ:~/MYSTIC$ cd ~/MYSTIC
david@SHIRAZ:~/MYSTIC$ chmod a+x install
david@SHIRAZ:~/MYSTIC$ sudo chmod a+x install
[sudo] password for david: 
david@SHIRAZ:~/MYSTIC$ 

I keep feeling like there is something intuitive I'm missing here.  Kind of like being asked to find butter in a refrigerator full of butter and not seeing it.  :p

[by the way, that cut and past thingy from the Terminal was great]
You can make it even greater by using code tags!

Then the contents will look like this:```
david@SHIRAZ:~/MYSTIC$ cd ~/MYSTIC
david@SHIRAZ:~/MYSTIC$ chmod a+x install
david@SHIRAZ:~/MYSTIC$ sudo chmod a+x install
[sudo] password for david: 
david@SHIRAZ:~/MYSTIC$ 

```The code tags can be found by clicking on the # icon (or by first clicking on *Go Advanced* if you don't see the # icon) or by typing the tags in yourself.

---

### Post by xpeaceservant on 2017-06-01
i think this requires a screen shot.
[ATTACH=CONFIG]275404[/ATTACH]
So in this folder, or file system, the Mystic install tells me when i run it that the "mystic" folder exists already. I'm guessing that happened from prior attempts at making a directory, or whatever. This time when I was at the directory where the install file is it ran when I typed ./install.  I don't know why, but it did.  The program then sets out all the file paths, etc. how it will install. It proceeds to say error and that the place I want to install exists already.

I noticed Xubuntu won't give me the choice to delete this folder.  I figured this would be a way to let the install function work easily.  How do I get it deleted or work to install it into the folder that is there already?

---

