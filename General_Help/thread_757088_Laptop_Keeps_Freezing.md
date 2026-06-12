---
title: "Laptop Keeps Freezing"
date: 2008-04-16
forum: General Help
---

### Post by gavinjb on 2008-04-16
Hi,

I have a Dell Inspiron 1525 Laptop and have been having a problem since I brought it that it will freeze every now and then, after watching the machine I have found that it tends to freeze when I am downloading large files from the internet (though it did freeze earlier when I was copying a large file to an external drive), I have found that when I download large files if I leave the machine alone it seems to be ok, but if I do anything else it has a chance of freezing.

The Laptop Spec is
Dell INspiron 1525
Intel X3100 Graphics Card
2gb Ram
160gb HD
15" 1440 x 900 Screen

Does anyone have any ideas, I have seen a few other posts on this forum, but none seem to cover my issues eactly.

Thanks,



Gavin,

---

### Post by sillyxone on 2008-04-16
heh, don't know about yours, but my Dell D620 and D630 doesn't have the cpu fan on by default. I had quite a lot of freezing at first until I found out that the fan doesn't run at all. I had to install i8kfan and add a script to run on startup and resume. No more freezing!

---

### Post by gavinjb on 2008-04-16
Thanks, how do I tell if the fan is on or not, I do here the fan come on at times, but do I need to look to see if there is any software to monitor it?

---

### Post by sillyxone on 2008-04-16
I had a Compaq V2000 before and Ubuntu can kick the fan on demand but so far, both the D620 and D630 has no automatic control. 

I think i8kfan can only control Dell laptop. I'm not sure how to check if the fan is controlled automatically or not. But you can try to see if having the fan on will solve the freezing: install i8kfan from Synaptic then run "i8kfan - 1" to have the fan run at low speed all the time.

---

### Post by gavinjb on 2008-04-16
Hi,

Do you have any extra repositories installed, as I am not seeing this app in synaptics.


Gavin,

---

### Post by sillyxone on 2008-04-16
it's part of i8kutils package (universe)

---

### Post by gavinjb on 2008-04-16
found the app in the repository apt-get install i8kutils and I can access the man pages, but when I try to run i8kfan I get 

```

can't open /proc/i8k: No such file or directory

```

So maybe I cant use it with my laptop


Gavin,

---

### Post by sillyxone on 2008-04-16
I just realized that the Inspiron 1525 has Ubuntu support officially from Dell, so I think the fan should be handled properly already. Sorry for leading you in a circle. 

If the laptop is shipped with Ubuntu and you still have warranty, it's best to contact their technical support. Otherwise, I think you can post your question in the Dell Community Forum ([http://www.dellcommunity.com/supportforums/board?board.id=sw_linux]("http://www.dellcommunity.com/supportforums/board?board.id=sw_linux"))

---

### Post by gavinjb on 2008-04-17
Just found this, not sure but it might be my answer.

[http://ubuntuforums.org/archive/index.php/t-746773.html](http://ubuntuforums.org/archive/index.php/t-746773.html)

---

