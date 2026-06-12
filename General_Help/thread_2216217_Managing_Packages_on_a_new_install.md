---
title: "Managing Packages on a new install"
date: 2014-04-10
forum: General Help
---

### Post by deamon_knight on 2014-04-10
I'm running Lubuntu 13.10 x86 on one system, and I wan to install Lubuntu 13.10 x64 fresh on a second system. I'm familar with Ubuntu style packages, but I'm looking for an easy way to install all the packages I've become accustomed too on this new system. As I understand it, If I use "apt-get install" and list several packages I can install all these packages at once, is there an easy way to list all the packages I have installed on my first system, save that list, and then pipe that list into an "apt-get install" on my new system, to install everything in one go. There are some packages I'm getting from PPAs or binaries, so I don't expect those to be done in one go, but those are the exception. Is this possible? Is there a concern for going from a 32bit to a 64bit install?

Thanks

---

### Post by bapoumba on 2014-04-10
[http://ubuntuforums.org/showthread.php?t=819396&p=5123565#post5123565](http://ubuntuforums.org/showthread.php?t=819396&p=5123565#post5123565)
The rest of the thread, even old, is worth a read.

---

### Post by papibe on 2014-04-10
Hi deamon_knight.

Here's another reference that adds a way to backup and restore your ppa's: [How To Backup Your Ubuntu Software]("http://www.matthartley.com/how-to-backup-your-ubuntu-software/").

Regards.

---

### Post by deamon_knight on 2014-04-11
I tried the dpkg method and it fouled up my system, not sure what went wrong there. Although I haven't tried it, shouldn't

<code>
sudo apt-get install < softwarelist.txt 
</code>

do what I'm looking for? Its generating the "softwarelist.txt" thats the question. Seems like it should be easier. Thanks for the link Papibe, I'll check it out.

---

### Post by oldfred on 2014-04-11
You need to use dpkg.

 From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade


 Some distro's cannot automatically get dselect (like Lubuntu)
apt-get install dselect

---

