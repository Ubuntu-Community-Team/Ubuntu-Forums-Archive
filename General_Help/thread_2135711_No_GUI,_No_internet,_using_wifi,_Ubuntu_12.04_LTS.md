---
title: "No GUI, No internet, using wifi, Ubuntu 12.04 LTS"
date: 2013-04-15
forum: General Help
---

### Post by xp15 on 2013-04-15
I installed 12.04 on my pc, and wanted to install the ATI driver for better performance. I discovered that my Card is not supported, and that my only option is the open-soucr driver for ATI.

I may have done some things wrong :D So, at start, the problem was:

"xinit unable to run server /usr/bin/x ubuntu."

I thought to purge the driver, and did this:

```
sudo apt-get purge fglrx*
```

and now, my new problem is this ^^ :
r```
oot@Pentium4:~# startx    #COMMAND
The Program 'startx' is currently not installed.you can install it by typing sudo apt-get install xinit"    #OUTPUT
```

Many solutions are abput installing again packages, like "ubuntu-desktop", the drievrs, "xinint" etc, but the Wifi is the problem, i can't download anything so I can't install anything.


Thanks for any help.
more information can be found here: [http://askubuntu.com/questions/281275/no-gui-no-internet-using-wifi-need-help](http://askubuntu.com/questions/281275/no-gui-no-internet-using-wifi-need-help)

---

### Post by QIII on 2013-04-15
*Moved to**&#8203; General Help***

---

