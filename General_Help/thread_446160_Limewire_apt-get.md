---
title: "Limewire apt-get"
date: 2007-05-16
forum: General Help
---

### Post by amrclutch1 on 2007-05-16
I see in different posts about installing limewire using apt-get, but I have no idea how people find what to type after "sudo apt-get", is there some program that you can search for the software you want to install and it will tell you or what? I am trying to install limewire basic if that helps any. Thanks for any help :)

---

### Post by AlanR8 on 2007-05-16
Just go to the limewire website and download the linux/debian version fro there....

---

### Post by celticbhoy on 2007-05-16
If you search google for "limewire basic linux" you will get alink to the official site download page. 
Just select what version you want 'Basic' 
then select 'no copyright material'
and .deb package will download to desktop
when downloaded double click to install

---

### Post by amrclutch1 on 2007-05-16
I have tried to install it that way, but it says it depends on "libc6" which is already installed, which is confusing, i googled it and found that people said apt-get takes care of this, is there another way to fix this?

---

### Post by amrclutch1 on 2007-05-16
No one knows? :(

---

### Post by sterilegenie on 2007-05-16
its as easy as sudo apt-get frostwire

---

### Post by Fabrique on 2007-05-25
~Whenever I try that I get the message

```
E: Invalid operation frostwire

```

---

### Post by jondecker76 on 2007-05-26
i think you need the medibuntu repository to apt-get limewire

---

### Post by strabes on 2007-05-26
sudo aptitude install frostwire

---

### Post by danne123 on 2007-06-17
> **strabes said:**
> sudo aptitude install frostwire

```
 sudo aptitude install frostwire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "frostwire"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by celticbhoy on 2007-06-17
Can you list the repo's you have setup.

---

### Post by danne123 on 2007-06-18
> **celticbhoy said:**
> Can you list the repo's you have setup.

How do, I do that?

---

### Post by mcduck on 2007-06-18
> **amrclutch1 said:**
> I see in different posts about installing limewire using apt-get, but I have no idea how people find what to type after "sudo apt-get", is there some program that you can search for the software you want to install and it will tell you or what? I am trying to install limewire basic if that helps any. Thanks for any help :)

Try searching with Synaptic Package Manager (System/Administration/Synaptic). Or the Add/Remove thing in Applications-menu.

If you can't find it in Synaptic, it's not in Ubuntu repositories or you have not enabled Universe & Multiverse (you can do that in System/Administration/Software Sources).

---

### Post by sumitc on 2007-06-18
the best thing is to get the software from the site.......here's the link
[http://www.limewire.com/download/download.php?version=linux_deb](http://www.limewire.com/download/download.php?version=linux_deb)

---

### Post by Kidge on 2007-06-18
sudo apt-get **install** frostwire

---

### Post by Maube-Not on 2008-02-01
Did you add the medibuntu repositories?

---

