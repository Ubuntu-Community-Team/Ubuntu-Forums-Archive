---
title: "Filesystem full but any file is consuming it"
date: 2022-12-18
forum: General Help
---

### Post by gurnisson on 2022-12-18
Hello! 

I am so newbie administrating linux and I'm trying to solve a "ghost" problem at home's ubuntu server virtualized through an esxi. I only use it to run docker containers (at the moment portainer, ouroboros and qbittorent).

I created an Ubuntu Server with (more or less) 80Gb virtual HDD. Some time ago, I've noticed that the volume "/dev/ubuntu--vg-ubuntu-/lv" ("/") was full and tried to find the files consuming space without results.

I had to expand the virtual HDD (executing lvextend and resize2fs) in order to be able to operate (update, etc) this server and grew it to 150gb, but i'm still trying to find the problem because I need to free this space.

You can see the results of the commands I used to investigate in case it helps: [https://termbin.com/5vbr9](https://termbin.com/5vbr9)

Someone could help me, please???

[EDIT] I forgot to say reboot didn't help.

---

### Post by gurnisson on 2022-12-18
After two weeks investigating...Found the solution myself just when I wrote this post. Sorry!!!

The problem was the NFS share I have mounted. I unounted it and.... ta-da!! the folder had 64gb of files. It makes no sense for me because there were files which are in the NFS but......erased it and solved the problem.

Now I have another doubt...It is any way to resize down to 80gb again the HDD?

---

