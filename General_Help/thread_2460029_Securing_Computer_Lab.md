---
title: "Securing Computer Lab"
date: 2021-03-31
forum: General Help
---

### Post by strictbishop on 2021-03-31
I work at a high school, and to squeeze some extra life out of some Chromeboxes that don't get updates anymore, we are thinking about installing Ubuntu on them. I've played around with one, and it seems to work pretty well on the hardware. One of the requirements for this computer lab is to run the "Secure Browser" for our state testing. Here's a [link]("https://ca.portal.cambiumast.com/") to it, it basically just requires Ubuntu 18.04 LTS with Gnome. 

What I came here to ask was, what steps should I take to secure these against students creaking havoc with them? I have seen some projects like Ofris(which seems old and outdated), other ideas were creating a Snap and running it on Ubuntu Core(which was a bit complicated when I tried to get all of the dependencies to work for the Secure Browser), or just creating a generic student login, which seems like the simplest solution to me. Is there a good way to make sure that any files or changes that a student made to the computer are erased on reboot? Obviously as long as they aren't a root user they can't do too much damage, but ideally I'd like to have it go back to a clean state every reboot.

Any advice would be greatly appreciated!

---

### Post by TheFu on 2021-03-31
You can script anything necessary.  The easiest thing would be to remove /home/s*/* at reboot and make all student accounts begin with an 's'.  Make the sudo/admin account begin with a non-'s' character.

As for security, there are thousands of things to know and only time + experience will gain that knowledge.  
Start here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
Learn about local user accounts so what is needed and what is optional for each.  You'd probably want to dynamically change the password daily for accounts like this too.

Really, there isn't any need to reboot a system.  I'd use ansible to remove every student account, delete the HOME, and recreate them as needed. Ansible would run from a trusted workstation.  Really, rebooting would be just a way to waste 2 minutes.  

Unix/Linux isn't Windows.  Reboot seldom is the correct answer.

You can script anything necessary either using ansible or just with simple ssh scripts. Your choice.  Ansible works over ssh.

I'm not a fan of Ubuntu Core (registration required to use?!!!) or snaps ( limited hardware doesn't like snaps).  Snaps break many things necessary for a corporate environment.

---

### Post by strictbishop on 2021-03-31
This is great info, thanks! I have used ansible a bit in the past so that may be a good option for pushing updates and config changes. 

I think wiping the home directories would accomplish most of what I’m looking for. I could probably set up a cron job to take care of this.

I’m fairly competent with Linux, so not too worried. I just was not finding a ton of up to date or simple setups for more of a “kiosk” type setup, which I don’t think is necessary. I’m always a fan of providing a computer that’s not locked down to the point of being useless to our students. 

Thanks again! Time to mess around with some scripting

---

### Post by TheFu on 2021-03-31
I suspect deleteing the HOME wouldn't be good. The "skel" files probably need to be there, like get places when a new userid is created. That's why I was thinking more about deleting a userid and recreating it when students were done.  Do they just walk in and sit or do they have to check in to have access? That would be important to know, since it could be integrated into the process to only delete-create when a new person shows up.  Then students could have access to their files for a full day, perhaps, assuming that wiping wasn't too quick.

Kiosk setups are completely different.  For those, I'd use a purpose-built TinyCore setup, but I'm assuming intel/amd CPUs. Are these chromeboxes ARM or Intel?

As always, there are 500 solutions. Only you can pick the best based on local knowledge.

---

### Post by strictbishop on 2021-03-31
The sessions are usually no longer than a few hours at most. Classes may come in and use the lab, and students are able to come use it on their break or lunch periods. 

I’ve looked at things like Porteus Kiosk, but I want to stick with distros supported by the secure test software, that’s kind of the most important thing. Ubuntu is great cause it’s on that list and my preferred 

The chromeboxes are intel thankfully. 

Wouldn’t deleting /home/s*/* wipe out those .skel files as well?

---

### Post by TheFu on 2021-03-31
> **strictbishop said:**
>  Wouldn’t deleting /home/s*/* wipe out those .skel files as well?

Exactly.  Some of my ideas aren't complete, but if your script puts a fresh set of those files back, then no harm.  I could see a student changing the default password, however.  Maybe deleting the account and re-adding it would be the best answer?

---

### Post by Impavidus on 2021-04-01
Anyone with physical access to the computer can get root access, although it may require a screwdriver to open the box. So you must trust your students to some extent.

If you make a generic student login and reset it to defaults every night, one student can still play tricks on a different student using the same computer the same day.

Another way to deal with this is giving each student his own login, with a home directory on some network attached storage. That way they can keep their files for the next day and can't mess with each other's files or the system. Group permissions can be used to allow students to cooperate on larger projects. It'll give the students some useful Linux skills. You'll need a few TB of storage on the network, depending on your number of students and the storage each one of them is allowed to use. You can set disk quota. The admin must be prepared to reset config files to defaults and passwords to temporary strings whenever some student messes up his own account (which will happen frequently) and implement a decent backup routine (which will be needed; people accidentally delete files all the time).

---

### Post by HermanAB on 2021-04-01
The least hassle would be to enable the Guest Account.

The guest account works like a kiosk and gets overwritten on each login.

---

### Post by TheFu on 2021-04-01
> **HermanAB said:**
> The least hassle would be to enable the Guest Account.

The guest account works like a kiosk and gets overwritten on each login.

I thought Ubuntu's guest account was deprecated due to security problems?

Students (or NASA engineers) can screw with others on the same LAN if they like.  I've heard rumors, but certainly wouldn't know anything about that first hand. <beg> Only heard about it from friends of friends through a cousin.

---

### Post by strictbishop on 2021-04-01
So after some trial and error, I came up with this > sudo find /home/student -not \( -name '.bashrc' -o -name '.profile' -o -name '.bash_logout' -o -name '.bash_history' -o -name 'student'  \) -exec rm -rv {} + which seems to do most of what I want as far as deleting the files. I set it up as a cron job to run at reboot

---

### Post by SeijiSensei on 2021-04-01
You can reconstruct the skeleton files by copying the contents of /etc/skel as the owner of the home directory.  All the files there are hidden, so you need to use "ls -a" to see them:
```

$ ls -la /etc/skel
total 48
drwxr-xr-x   3 root root  4096 Jul 16  2020 .
drwxr-xr-x 159 root root 12288 Mar 31 16:25 ..
-rw-r--r--   1 root root   220 Feb 25  2020 .bash_logout
-rw-r--r--   1 root root  3771 Feb 25  2020 .bashrc
drwxr-xr-x   2 root root  4096 May 18  2020 .config
-rw-r--r--   1 root root 14965 Feb 21  2020 .face
lrwxrwxrwx   1 root root     5 Apr 13  2020 .face.icon -> .face
-rw-r--r--   1 root root   807 Feb 25  2020 .profile

```

---

### Post by HermanAB on 2021-04-01
Just delete and recreate the user, that will copy the /etc/skel files back.

---

### Post by strictbishop on 2021-04-01
Yeah that was my other thought, which may actually be a lot simpler than the other way of deleting everything but the skel files

---

