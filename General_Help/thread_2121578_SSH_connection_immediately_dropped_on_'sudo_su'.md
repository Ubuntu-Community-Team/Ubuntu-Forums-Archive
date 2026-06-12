---
title: "SSH connection immediately dropped on 'sudo su'"
date: 2013-03-02
forum: General Help
---

### Post by Contrarian on 2013-03-02
I cloned two machines from a base template I created of 12.10 Server.  The template had nothing installed except openssh. Because I am running this on a 2008 Hyper-V box, I added hv_vmbus, hv_storvsc, hv_blkvsc, hv_netvsc to /etc/initramfs-tools/modules (I have done this with previous versions of Ubuntu Server, so I do not think this is the root cause).  

I created two servers, *mail2 *and *mail3*.  Updated their IP addresses and hostnames.

When I SSH into *mail2 *I can connect and browse around, run commands, it works fine as far as I can tell. However when I **sudo su **it immediately disconnects the connection.  If I connect to the machine via the Hyper-V console, **sudo su** works just fine.  It's only when I connect via SSH does trying to gain SU access does it terminate my connection.  This same behavior doesn't happen on *mail3 *however.  

Because the two are based off the same template, I don't necessarily think it's a configuration issue. The only thing I figured may be the cause is a corrupted ~/.bashrc in the root home directory, but changing the ~/.bashrc to ~/.bashrc_old doesn't change the behavior.   And because I can initially connect and work on mail2 as a regular user account, I don't think it's a TCP/IP configurations issue.  So I'm a little stumped as to where to look.  

I"m mostly curious how I can troubleshoot this over what the root cause is.  Where might I go to look for error messages of why a terminal session is being suddenly dropped?  

Thanks!

---

### Post by rnerwein on 2013-03-02
hi
i think i can bet there is a "set -e" anywhere. i did here on my box the following in my user "testuser".
i edit his .bashrc and insert following:
# ~/.bashrc: executed by bash(1) for non-login shells.
[COLOR=#ff0000]set -e[/COLOR]
.....
then i run in his home:

[COLOR=#ff0000]root[/COLOR]@tschang:/home/surfer# . ./.bashrc (have a look at the user - run befor the modification i ran su - root - was root before !!!)
[COLOR=#006400][/COLOR]
and now be back in my account:
richi@tschang:~ 18:22->   ( the su session is canceled and i am back in my home).
comment out the "set -e" and it works !
[COLOR=#006400]root[/COLOR]@tschang:/home/surfer# su - testuser
[COLOR=#006400]testuser[/COLOR]@tschang:~$ 


this behavior is although given when i use set -e in the .bashrc and try to open a new terminal - terminal shown up and immediatly gone !
but i ain't have this behavior when i do the same joke in root's .bashrc. 
to debug your problem use "set -x" (this set the shell to debug-mode) in the procedures which will run when you are using 
the "su - root" ( best in the /root/.bashrc ).
have much fun when you search for this problem ;-)
ciao

---

### Post by Contrarian on 2013-03-02
So, I noticed on "mail3" that there were 11 pending updates, and I did an update of the template and "mail2" earlier in the week.  After I ran the system updates on "mail3", the same error happened on that box as well.  Looking at the 11 updates, one of them was for sudo (1.8.5p2-1ubuntu1.1) - so I think that the update broke something.

---

### Post by Contrarian on 2013-03-02
rnerwein, 

Thanks.  

I was able to correct this on "mail3" by downloading and installing **sudo_1.8.6-8_amd64.deb** from [http://www.sudo.ws](http://www.sudo.ws).   It looks like the current package being released may have a bug affecting my particular installation, so I'll see if I can post that information up the food chain that they may get the latest version out if anyone else has this issue.

C

---

### Post by rnerwein on 2013-03-02
hallo
i got similar problem on a solaris high-end !!!!! server (about 12 years ago) and that takes me a time to solve it ( my professional is "trouble shooting and performace).
to make it easier to debug such problems down see the thread i will open now (will call the thread: set -e and the possible dangerouses - ups. i think you are not allone.
ciao
       richi

---

