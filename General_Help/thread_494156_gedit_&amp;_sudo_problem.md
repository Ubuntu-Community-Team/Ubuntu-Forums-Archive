---
title: "gedit &amp; sudo problem"
date: 2007-07-06
forum: General Help
---

### Post by bbmak on 2007-07-06
I am using Xubuntu

I am trying to directly edit a text file with gedit in /etc/
However, i cannot save the file due to the sudo permission.

So, what i do is to save the file into the desktop and then use the Terminal to copy the file to the directory.
sudo cp /home/username/Desktop/....  /etc/


Are there anyway i can use gedit with sudo permission????

---

### Post by stchman on 2007-07-06
> **bbmak said:**
> I am using Xubuntu

I am trying to directly edit a text file with gedit in /etc/
However, i cannot save the file due to the sudo permission.

So, what i do is to save the file into the desktop and then use the Terminal to copy the file to the directory.
sudo cp /home/username/Desktop/....  /etc/


Are there anyway i can use gedit with sudo permission????

You should be able to:

sudo gedit <file name>

This will bring up the text editor and allow you to edit and save.

I use this method all the time.

If I remember correctly Xubuntu does not come with gedit installed.  Did you install it?

---

### Post by p_quarles on 2007-07-06
> sudo gedit <file name>

That will work, but the general rule for running graphical apps with root permission is to use ```
gksu {name-of-app}
```

That's a handy little feature that will decide--based on which app you run with it--whether to run it using "su" or "sudo."

---

### Post by bbmak on 2007-07-06
> **stchman said:**
> You should be able to:

sudo gedit <file name>

This will bring up the text editor and allow you to edit and save.

I use this method all the time.

If I remember correctly Xubuntu does not come with gedit installed.  Did you install it?

I have to install gedit by myself.

---

### Post by bodhi.zazen on 2007-07-06
In ubuntu it is gksudo (as opposed to gksu)

So, ```
gksudo gedit <file>
```

---

### Post by Ayuthia on 2007-07-06
> **bodhi.zazen said:**
> In ubuntu it is gksudo (as opposed to gksu)

So, ```
gksudo gedit <file>
```

But both gksu or gksudo should work because gksudo is a link to gksu.

---

### Post by smoker on 2007-07-06
i think > sudo mousepad <file> would work in xubuntu without having to download gedit

edit: it does, just tried it!

---

