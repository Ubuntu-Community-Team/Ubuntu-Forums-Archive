---
title: "Gedit in feisty doesn't automaticlly save"
date: 2007-04-23
forum: General Help
---

### Post by Neuralgia on 2007-04-23
I upgraded from Edgy.

Beryl dissapeared. Used to work 100% in Edgy.

I want it back.

I'm following instructions from "http://ubuntuguide.org/wiki/Ubuntu_Feisty#Eye_Candy"

On the step to create the "startxgl.sh" file, usin gedit, when I click in SAVE, I get this mssg.

> Could not save the file /usr/local/bin/startxgl.sh.

Unexpected error: File not found

This never happened in edgy. If a file didn't existed, it just created it.

Am I doing something wrong? What changed in Feisty that doesn't allow me to create a new file?

I miss my Beryl :(

---

### Post by justinjstark on 2007-04-23
When I try to save that file, I get the correct error:

> Could not save the file /usr/local/bin/startxgl.sh.
You do not have the permissions necessary to save the file.
Please check that you typed the location correctly and try again.

Which is what it should be because as a user, I do not have write permissions to that directory.

Are you running gedit as root?

---

### Post by Shazaam on 2007-04-23
justinstark beat me to it
This might be a stupid question but are you running gedit as root?    gksudo gedit

---

### Post by justinjstark on 2007-04-23
Hmmm, it saves fine for me if I run gedit as root.  I didn't have that file before either.

You could try using vim:

```
sudo vim /usr/local/bin/startxgl.sh
```

Press the insert key to insert text.  Then when you are done, press esc and then :wq to save and quit.

---

### Post by Neuralgia on 2007-04-23
yes, I'm using SUDO... I just tried GKSUDO (even though I don't know what the difference is) an didn't work either.

any ideas?

---

### Post by justinjstark on 2007-04-23
Another option would be to touch the file to create it and then you should be able to edit it with gedit as root.

```
sudo touch /usr/local/bin/startxgl.sh
sudo gedit /usr/local/bin/startxgl.sh
```

---

### Post by justinjstark on 2007-04-23
> **Neuralgia said:**
> yes, I'm using SUDO... I just tried GKSUDO (even though I don't know what the difference is) an didn't work either.

any ideas?

FYI: GKSUDO is just a graphical frontend to sudo.  So, if you use gksudo you will get a popup asking for your password rather than the command line.  They both have the same effect.

---

### Post by Neuralgia on 2007-04-23
> **justinjstark said:**
> Another option would be to touch the file to create it and then you should be able to edit it with gedit as root.

```
sudo touch /usr/local/bin/startxgl.sh
sudo gedit /usr/local/bin/startxgl.sh
```

This is getting weird.

look what happens with touch

> danielcifuentes@OBELIX:~$ sudo touch /usr/local/bin/startxgl.sh
touch: cannot touch `/usr/local/bin/startxgl.sh': No such file or directory
danielcifuentes@OBELIX:~$ sudo gedit /usr/local/bin/startxgl.sh

** (gedit:8126): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
danielcifuentes@OBELIX:~$ 


---

### Post by justinjstark on 2007-04-23
What are the output of these?:

```
ls -l /usr/local | grep bin
```

```
mount -l
```

---

### Post by Neuralgia on 2007-04-23
just in case

[IMG]http://img201.imageshack.us/img201/7350/screenshot1cb6.png[/IMG]

---

### Post by Neuralgia on 2007-04-23
sorry, replied at the same time you did

[IMG]http://img217.imageshack.us/img217/3235/screenshotdanielcifuentoa9.png[/IMG]

---

### Post by justinjstark on 2007-04-23
It appears as though you do not have a /usr/local/bin.  I'm not sure if that's a problem but you could try creating it.

```
sudo mkdir /usr/local/bin
```

Then try to touch the file:

```
sudo touch /usr/local/bin/startxgl.sh
```

---

### Post by justinjstark on 2007-04-23
Alternatively, you could put startxgl.sh in /usr/bin rather than /usr/local/bin.  It's not the best practice but should work fine.

---

### Post by Neuralgia on 2007-04-23
FINALLY

thanks a lot.

Now, the question is... why didn't I have that folder? and how did you realized that?

Why did I had it in Edgy, and now on Feisty is gone?:confused:

---

### Post by justinjstark on 2007-04-23
> **Neuralgia said:**
> FINALLY

thanks a lot.

No problem, I'm glad we figured this out.

> Now, the question is... why didn't I have that folder?

/usr/local/bin might not exist unless an application installs to that directory.  Few applications do.

> and how did you realized that?

The code *ls -l /usr/local | grep bin* says display the directories within /usr/local and search for any directory that contains "bin".  Since you only had sbin and not bin, it was pretty obvious.

```
justinjstark@alf:~$ ls -l /usr/local | grep bin
drwxr-xr-x  2 root root 4096 2007-04-23 22:24 bin
drwxr-xr-x  2 root root 4096 2006-11-10 14:23 sbin
```

> Why did I had it in Edgy, and now on Feisty is gone?:confused:

Who knows.  **** happens.

---

