---
title: "I destroyed my system"
date: 2006-09-17
forum: General Help
---

### Post by CameronCalver on 2006-09-17
Hello today i was just doing a routine download of some things including games and multimedia software and i left the room for it to download and when i came back i found that it has installed many system things eg i cant get into synaptic it says gksudu does not exist.
I would like to do a complete reistall anyway but i would like to keep things like make makedepend and basicly everything i have ever downlaoded through apt-get and synaptic and i have already backed up my homefolder.
So if there way i can do a full reinstall and then uncompress a file on a computer on my lan do a restart and have everything back again

---

### Post by sktx on 2006-09-17
What I think I would do, in your position, is:

1) Back up the contents of /var/cache/apt/archives/
```
tar -cf ~/aptcache.tar.gz /var/cache/apt/archives/*
``` 
2) Copy the backup that you just made from /home/<user>/aptcache.tar.gz to somewhere safe that won't be overwritten on reinstall...

3) Reinstall Ubuntu

4) Move the aptcache.tar.gz file back to the archives dir (the command below assumes that it's in your home directory).
```

sudo mv ~/aptcache.tar.gz /var/cache/apt/archives

``` 
...and unpack it:
```

cd /var/cache/apt/archives
sudo tar zxvf aptcache.tar.gz

``` 
5) If everything works out alright and the .deb files are unpacked to the archives dir, remove the backup tar with:
```

sudo rm aptcache.tar.gz

``` 
You then should be able to reinstall whatever you need without having to go through the pain of downloading it again, assuming that you don't have synaptic set to delete the packages you've downloaded after they've been installed.

Hope this helps.  Let me know if you need any more help.

---

### Post by CameronCalver on 2006-09-19
nope wont work coz i apt-get clean once a month

---

### Post by sktx on 2006-09-19
Hrmm.. well, as far as I know, that means you're S.O.L... That leaves you with "installing from scratch."

You have /home on a separate partition?

---

### Post by CameronCalver on 2006-09-19
nope i just backed up my /home onto another computer on the lan then re installed then put it back on and updated

---

### Post by sktx on 2006-09-19
Well, one of the things that I do (and that more than a few other users do) is to put their /home directory on its own partition.  That way, if you have to reinstall, you don't have to worry too much about losing your data.  I've had the same home folder through about 10 installs of Ubuntu. 

Another thing some users do is to mount their /var /tmp and /usr dirs on separate partitions, although some users might call this overpartitioning.  partitioning /tmp, though, does prevent an attacker or a bug from using it to fill up your drive.  It's also not a bad idea to set the nosuid,noexec,nodev options on /tmp in your /etc/fstab

---

