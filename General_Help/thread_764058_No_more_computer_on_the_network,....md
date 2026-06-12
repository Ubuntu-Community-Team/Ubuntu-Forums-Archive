---
title: "No more computer on the network,..."
date: 2008-04-23
forum: General Help
---

### Post by Cygoku on 2008-04-23
My laptop is under Gutsy.  Until yesterday, my desktop was on WindowsXP.  Both computer could see each other file, share documents and folders.  Now my desktop is running Hardy Heron RC and it stop working.

Cygoku

---

### Post by ryanhaigh on 2008-04-24
Have you setup samba (or whatever sharing protocol you want to use), do both still have network connectivity, can you ping between them?

---

### Post by Cygoku on 2008-04-24
No, there is no "samba" installed on neither one of them ... Should I ?? And yes they can both ping each other.

Cygoku

---

### Post by retrow on 2008-04-24
Yes, you'll need to install samba, and (someone correct if I am wrong on this) samba-client. Then you might need to restart the program.

```
sudo apt-get install samba samba-client
```
```
sudo /etc/init.d/samba restart
```

Then in Hardy, you'll need to give share permissions and share name to the folder you wish to share over the network. That should be it.

---

### Post by Iowan on 2008-04-24
I can't speak for Hardy, but my other Ubuntu installations come with samba-client installed. Although they have a **/etc/samba/smb.conf** file, samba-server is not pre-installed.

---

### Post by Cygoku on 2008-04-25
To what I can understand, there is really some stuff to install.  Under GNOME, of you go to System >> Admin >> Shared Folders, it will tell you what is missing/not-installed to complete the task.  

I just need the Hardy Heron repositories to be back up again.

Cygoku

---

### Post by chrisccoulson on 2008-04-25
There is no System -> Administration -> Shared Folders application on Hardy. Samba shares are handled by a Nautilus extension (which should be preinstalled) which makes use of Samba's usershare functionality. Just pick a folder in Nautilus, right click and go to Properties, and there should be a sharing tab. If Samba is not installed, you should get prompted to install it.

---

### Post by greyghost60 on 2008-04-26
Thanks that all worked but the other machine wants a password and I have tried both PC A's and PC B's but they don't work. I haven't set any other password so what it looking for. The only way round it seems to be as a guest. Confused

---

### Post by 3rods on 2008-04-26
I can also confirm this issue in hardy. Nautilus knows there is a window's network, but it doesn't list any PC's. I have installed the samba server (which shouldn't be needed because I'm not serving a share) and I've change my work group in the smb.conf file. 

I can't mount shares from XP with cifs, but if I install smbfs I can mount the XP share (by IP address). I thought smbfs was deprecated in favor of cifs??? 

Could not being able to list network nodes be because it can't find the hostname? **Doesn't samba need to 'look-up' the hostname?** If I ping the host, if can't resolve it - just a thought. I forget how to check/fix hostname lookups.  

tl;dr  I can ping the computer from my ubuntu machine to the XP machine. I can't list the network.

---

### Post by ryanhaigh on 2008-04-26
3rods:
To lookup hostnames for samba shares netbios is used. To lookup a computer by its netbios name use ```
nmblookup hostname
```. 

greyghost60:
Because by default samba is configured to use user level security you will need to add users to sambas user/password database, there may be a gui way to do this but I do not know it. From the commandline you can do:
```

sudo smbpasswd -a yourusername
sudo smbpasswd -e yourusername

```
You can then use the password you assign here to access your shares.

---

### Post by greyghost60 on 2008-04-27
Many thanks Ryan

---

### Post by 3rods on 2008-04-28
> **ryanhaigh said:**
> 3rods:
To lookup hostnames for samba shares netbios is used. To lookup a computer by its netbios name use ```
nmblookup hostname
```. 

That works, but I still can't see my networked XP boxen. I can ping and mount by IP, but can't browse. I also reset the XP fire wall and no luck. I'm not running any sort of A/V or Zone Alarm garbage either.

---

### Post by Cygoku on 2008-04-29
Wow, that was easy.

Gutsy, Sytem >> Administration >> Shared Folders ... promts you to install stuff and you are done, then restart.  

Hardy, right click on any folder, choose the sharing option ... promts you to install stuff and you are done, then restart.  

...

My only problems now is that it doesn't allow to copy/paste files or folders to the other (Gutsy>Hardy or Hardy>Gutsy).

Cygoku

---

