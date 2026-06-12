---
title: "Matlab R2006b install problem (Segmentation fault)"
date: 2007-03-20
forum: General Help
---

### Post by PeterC on 2007-03-20
Hi,

I'm trying to install Matlab R2006b on Kubuntu 6.10.

This is what I have done:

1. Mounted CD1 on /mnt/isoimage
2. Created /usr/local/matlab73
3. Copied license file to /usr/local/matlab73
4. Changed directory to /usr/local/matlab73
5. Started installer: /mnt/isoimage/install* -t
6. Accepted 'Software License Agreement'
7. Now, the installer asks: Enter the MATLAB root directory > [/usr/local/matlab73]
   I hit ENTER, and then this error shows up: Segmentation fault

   The installer stops

I don't know how to handle this error. Does anybody have an idea?

Thanks for any help

---

### Post by ehowell on 2007-03-20
I have been successful installing matlab 2006b (and now 2007a) on *buntu, but have had some troubles if I do not invoke the install with the sudo command. What are the file permissions on the /usr/local/matlab73 dir?

Just remember to make sure that you authorize your normal username or else root may be the only one that can run matlab afterwards (assuming single user license). Or you can hand edit the MLM.opt file later (in /usr/local/matlab73/etc).

Other than that, I'm not quite sure, but first (and simple) things first, as it didn't look like you used the sudo command :)

---

### Post by PeterC on 2007-03-21
Thanks for the reply.

You are right, I did not use the sudo command.
However, I did it from a root-shell (I guess that has the same affect?).

I have now tried to use the sudo command as you suggested.
Unfortunately, the result is the same :(

---

### Post by PeterC on 2007-03-27
Self-reply.

I found a solution.

The installer does not work properly when I am logged on as root.

However, the installation works perfectly when I:
1. Change read/write permisions of
   - '/usr/local/temp'
   - '/usr/local/matlab73'
   - '/usr/local/bin'
   so a normal user can write to these directories.
2. Start the installer as a normal user (not root).

---

### Post by Geir102 on 2007-03-28
hi any one know if its possible to install matlab to /media/data/   Antother partition that is. Cant get it to work

---

