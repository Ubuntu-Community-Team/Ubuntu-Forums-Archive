---
title: "Comodo Antivirus software"
date: 2014-08-18
forum: General Help
---

### Post by john_burns2 on 2014-08-18
After a few problems viewing some websites, I thought I might have some sort of virus (highly unlikely) so installed Comodo Antivirus. Downloaded the .deb file from the Comodo website and installed it through the software centre. After it had installed I ran the /opt/COMODO/post_setup.sh, command, then the /etc/init.d/cmdavd restart command, in a terminal. Everything is supposedly happy. but now websites, email etc run slowly (probably because Comodo is scanning them) I now want to uninstall this program, but the software centre doesn't find Comodo under installed programs. It doesn't even recognise Comodo on anything. 
Anyone have any ideas how to uninstall it (preferably without breaking down in tears) 

Cheers

JB

---

### Post by slickymaster on 2014-08-18
That's weird since according to the Comodo site they supply a .deb package which would have been installed with the software-center unless you used another application or installed from another package type.

Anyway, you can try:```
sudo apt-get --remove purge cav-linux
```

---

### Post by papibe on 2014-08-18
Hi john_burns2.

I haven't install Comodo myself but this is what I would do:

After searching for 'Comodo' on the 'Software Center', try looking on the link 'technical packages' on the bottom of the window.

If that doesn't work try this to see how the package is named:
```
dpkg -l | grep -i comodo
```
Once you get the name, say 'comodo-av', you can remove it like this:
```
sudo apt-get purge comodo-av
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by john_burns2 on 2014-08-18
Thank you slickymaster. Comodo now removed. Yes I did download the .deb file from their website (and it was called cav-linux) and used the Ubuntu Software Centre to install it. Can't for the life of me understand why it couldn't find it once installed. I even looked in the installation history and it simply wasn't there (even though I only installed it yesterday) History told me the last thing installed was an update on the 12th of August. I can only assume it hides itself from everything??Once again,, Thank you.

---

### Post by slickymaster on 2014-08-18
You're welcome. Glad you got it fixed.

Happy *buntuing.

---

