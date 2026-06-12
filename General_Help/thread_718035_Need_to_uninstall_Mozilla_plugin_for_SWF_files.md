---
title: "Need to uninstall Mozilla plugin for SWF files"
date: 2008-03-07
forum: General Help
---

### Post by durkhrod chogori on 2008-03-07
Can anyone tell me how to do it because it's not possible to do it via Synaptic?

I am trying to watch YOUTUBE vids and got installed the Adobe flash plugin but the repos plugin not only doesn't do anything but crashes FF and Ubuntu as well.

I need to remove "swfdec-mozilla" and "swf-player"?

Does anyone know the command entries for that?

Thanks in advance.

---

### Post by azadpanchi on 2008-03-07
Is firefox closed when you try to use synaptics to remove flash plugin?  Make sure it is closed.

Any package you want to remove in synaptics just find out the name and you can use the following command:
sudo apt-get remove *package*

If you receive any errors please post it here.

---

### Post by PinkFloyd102489 on 2008-03-07
And to watch flash videos on YouTube, install flashplugin-nonfree.

---

### Post by durkhrod chogori on 2008-03-07
> **azadpanchi said:**
> Is firefox closed when you try to use synaptics to remove flash plugin?  Make sure it is closed.

Any package you want to remove in synaptics just find out the name and you can use the following command:
sudo apt-get remove *package*

If you receive any errors please post it here.

I closed FF, tried that command and got this message:

[IMG]http://i31.tinypic.com/bx2f5.png[/IMG]


Note: what I am trying to remove is the following:

**swfdec-mozilla** & **swf-player**

Thanks

---

### Post by durkhrod chogori on 2008-03-08
Deleted.

---

### Post by durkhrod chogori on 2008-03-08
Deleted.

---

### Post by otrojake on 2008-03-10
I saw from your screenshot that when you ran the 'apt-get remove' commands, you had the Synaptic Package Manager open.  You'll need to have that closed when you run those commands.

First, close Synaptic.  Then run this command:

> sudo apt-get remove swfdec-mozilla swf-player

If that doesn't work, you can paste the errors resulting from that code here and then we'll see what we can do to help.

---

