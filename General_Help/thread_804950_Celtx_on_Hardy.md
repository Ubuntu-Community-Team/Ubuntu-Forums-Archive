---
title: "Celtx on Hardy"
date: 2008-05-23
forum: General Help
---

### Post by macanations on 2008-05-23
I've downloaded and extracted the screen-writing program [Celtx]("http://www.celtx.com") on Ubuntu 8.04, but whenever I try to launch the program with the bash script, it says that I am missing libsmime3.so.  However, when I look in my /usr/lib/ directory, libsmime3.so.1d is already there.  I don't know if that means there is a naming issue or what.

Can anyone help me figure out how to get this program working?

Thanks!

---

### Post by jrothwell97 on 2008-05-23
Mysteriously, I've only been able to get Celtx to work properly as root. Try running

```
sudo /usr/local/celtx/celtx
```

in a terminal. It's not ideal, but I've got no idea why it won't access the libraries as a normal user.

---

### Post by macanations on 2008-05-23
Running as root doesn't seem to help for me - I still get the same error message.

---

### Post by Dannyblueyes on 2008-05-26
I had so many issues with this program I eventually downloaded the windows version and ran it in WINE. Seems to work fine now.

---

### Post by macanations on 2008-05-30
Using wine worked.  Not the best solution but it will do for now.  Thanks.

---

### Post by shellmich on 2008-06-14
The following assumed that you installed celtx as root in order to let all users on your Ubuntu machine have access to it (see also [http://wiki.celtx.com/index.php?title=Installation]("http://wiki.celtx.com/index.php?title=Installation")).

After this you should be able to start Celtx with: ```
sudo /usr/local/celtx/celtx
```

If you now want to be able to start celtx without sudo, you have to remove the subfolders .greyfirst and .celtx as described in the celtx wiki.

These folders should be in your home directory (~) but they are hidden and - as you have installed celtx as root (with sudo) - you can only remove them as root. One way to do this is to start Nautilus as root with: ```
sudo nautilus
``` Select your home folder, choose "show hidden files" (CTRL + H) and remove both folders.

Afterwards, any user should be able to run celtx using ```
/usr/local/celt/celtx
```
Note: If you want launch celtx from an icon, you could e.g. add a custom application launcher to your upper panel.

BTW - After [http://brainstorm.ubuntu.com/idea/3962/]("http://brainstorm.ubuntu.com/idea/3962/") has been realized, installing celtx should become as easy as it should :).

---

### Post by ex.hav0k on 2008-06-27
> **Dannyblueyes said:**
> I had so many issues with this program I eventually downloaded the windows version and ran it in WINE. Seems to work fine now.

haha, if you're going to use wine, just use finaldraft.

and you guys should have read the celtx wiki...

---

### Post by 500cuts on 2008-09-14
I just extracted the files to a folder, cd'd to that folder and did:

sudo ./celtx

Works great.

---

