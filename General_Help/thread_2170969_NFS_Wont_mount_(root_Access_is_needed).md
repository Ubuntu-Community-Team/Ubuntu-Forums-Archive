---
title: "NFS Wont mount (root Access is needed)?"
date: 2013-08-28
forum: General Help
---

### Post by chrisbarnes1992 on 2013-08-28
Recently i have got a freebie laptop and decided to run Kubuntu 13.04 on it. 
Install went well, Got all of the programs etc i needed. Cool.

However I needed to get to all of my documents on my File Server.

I typed out the same bits of info for the NFS mounts on /etc/fstab as my 13.04 netbook. Which works everytime.

Then re-booted my Laptop and when i opened Dolphin and clicked on the Share it said.

> An error occurred while accessing 'Home', the system responded: mount:  only root can mount 192.168.1.200:/mnt/twin80 on /mnt/data 

I thought it was odd and decided to go to the terminal and use ls in the mount point and nothing.

After checking fstab again rebooted again. Still same error messages. And the lack of stuff in the directory. 

Here is the blurb i added to fstab.

> 192.168.1.200:/mnt/twin80  /mnt/data    nfs          rsize=8192,wsize=8192,timeo=14,intr,auto,nosuid 0 0

Does anyone have any ideas what is going on as i have the same basic info one more than one computer and they work fine. (Debian XBMC Box and Ubuntu Netbook)

Have done a fair bit of searching for the answer but no luck so far. 

Thanks in Advance,

---

### Post by Feathers McGraw on 2013-08-28
Hi,

Just a couple of things to check:

1) you have created the directory /mnt/data ?

2) your hard drive is unencrypted?

Feathers

---

### Post by SeijiSensei on 2013-08-28
What user owns /mnt/twin80 on the server?  What are its permissions?  Is the share world-writable?

Is the UID assigned to your user on the client machine identical to your UID on the server?

What errors do you see on the server when you try and mount the share?  Look in /var/log/syslog or /var/log/messages.

---

### Post by chrisbarnes1992 on 2013-08-28
Hi there,

To answer the questions.

> What user owns /mnt/twin80 on the server?  What are its permissions?  Is the share world-writable?

What ever the FreeNas server sets it up as. It has got Read / Write set on the share options.

> You have created the directory /mnt/data ?

Yes and it even gave it the command sudo chmod -R 777 /mnt/data as a test stil no luck.

> Your hard drive is unencrypted?
 
Unencrypted. Never botherd with encryption.

> Is the UID assigned to your user on the client machine identical to your UID on the server?
 
To be honest i dont know. All i did in FreeNAS is setup the share made it Read / Write and connected my other computers to it and it worked fine.

> What errors do you see on the server when you try and mount the share?  Look in /var/log/syslog or /var/log/messages.

In progess in trying to get a copy of the log from FreeNAS to show you A.S.A.P

---

### Post by nerdtron on 2013-08-28
I'm using NAS4Free with an NFS share too. Haven't tried to add an fstab entry yet. But can you mount the NFS share manually using the command line?

```
sudo mount 192.168.x.x:/mnt/share /local/folder
```

If so, then maybe you can add the command to your startup entry.
Also here is my screenshot of the nfs share. All pc on the network 192.168.7.0/24 will be able to mount the share.
[ATTACH=CONFIG]245809[/ATTACH]

---

### Post by chrisbarnes1992 on 2013-08-29
Tried 
> sudo mount 192.168.1.200:/mnt/twin80 /mnt/data

and its saying rong fs type. bad option, bad superblock.

On my FreeNAS NFS options root access is allowed and the IP Range has been added. 

It is a bit odd that other Linux PC's connect perfectly and yet this one wont.

---

### Post by steeldriver on 2013-08-29
Did you install the nfs-common package on the new machine?

---

### Post by chrisbarnes1992 on 2013-08-29
I did install nfs-common with a  vast of other programs etc at the same time. 

Would it be worth removeing it and reinstalling it. Something like 
> sudo apt-get --purge remove nfs-common && sudo aptget update && sudo apt-get install nfs-common -y

---

### Post by steeldriver on 2013-08-29
What actual nfs exports do you see with showmount?

```
showmount -e 192.168.x.x
```

where .x.x is your server

---

### Post by chrisbarnes1992 on 2013-08-29
Nothing Happens.

---

### Post by nerdtron on 2013-08-29
sudo apt-get install nfs-common
sudo apt-get install nfs-kernel-server


The second command solved my problem in wrong fs type.

---

### Post by chrisbarnes1992 on 2013-08-29
I ran both commands and found nfs-common was already installed and it did nothing. Then ran sudo apt-get install nfs-kernal-server, re booted and it worked. Not sure why Kubuntu wanted both nfs-common and nfs-kernal-server to access the files. 

Is it just a Kubuntu thing as Ubuntu and Debian works fine with just nfs-common?

---

### Post by nerdtron on 2013-08-29
> **chrisbarnes1992 said:**
> I ran both commands and found nfs-common was already installed and it did nothing. Then ran sudo apt-get install nfs-kernal-server, re booted and it worked. Not sure why Kubuntu wanted both nfs-common and nfs-kernal-server to access the files. 

Is it just a Kubuntu thing as Ubuntu and Debian works fine with just nfs-common?

I don't think it's just Kubuntu. I need to install the nfs-kernal-server to a Ubuntu server in order to mount an NFS share. I don't know why the nfs-common is not enough. If you read the documentation in Ubuntu, it says that the client will only need the nfs-common package and that nfs-kernal-server is for the NFS server only. Obviously it's not true (in my case).
But at least you sorted out the problem.
:)

---

### Post by SeijiSensei on 2013-08-30
The machine I'm using right now is an NFS client and only has the nfs-common package installed.  I've got a couple of other machines running Kubuntu 13.04; they all have just nfs-common installed.  My NFS server is running on CentOS 5.8.

---

### Post by chrisbarnes1992 on 2013-08-30
Hmm, At this moment in time it is working fine so i am just going to leave it alone. Lol. Its auto mounting on system start up with the little blurb I mentioned earlier in the thread with fstab. Which is what i prefer to do as i forget to mount them when i really need it. 

I dont think i will bother to look into the reason why it wants both the server and client packages at the same time. As 13.10 is Just around the corner and i plan to upgrade to it. :-). 

Thanks for all of the help,

---

### Post by gizmojunkee on 2013-09-03
Hi

I got a similar issue and by the hang of it I can't figure it out.
- I installed a clean Ubuntu 12.04 Server edition in parallels. 
- I run the update
- now installed (nfs-common, port map, nfs-kernel)
- and created a dir in /mnt/TEST
- next I setup a new Share on my Synology DSM
- now I executed the following command on the client
  sudo mount -v -t nfs 192.168.12.23:/volume1/TEST /mnt/TEST
- I am always getting a mount(2) connection timeout.

If I execute showmount -e 192.168.12.23 I can see the available mounts.

And now the worst, if I try the same command on my Mac it monts the nfs share right away.

Any idea?

---

