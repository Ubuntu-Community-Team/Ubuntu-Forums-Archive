---
title: "purging all kernel related files (image[-signed], headers, generic etc) except latest"
date: 2017-10-11
forum: General Help
---

### Post by kerrygee on 2017-10-11
Hi,

i am looking for a way to purge all kernel images (signed and not-signed) and headers except for the latest one. by latest i dont mean the currently used, but the really latest installed on the system. there should only be the most recent left and used on the system. I know there is  "apt autoremove", but it will leave always two versions on the system. i know this is for security reasons, just in case the latest will make trouble, but in my case its perfectly ok to have only one. today i made a update and it lift the kernel version to "4.10.0-37", so had to remove the elder one manually by hand with the command:

"apt remove linux-image-4.10.0-35-generic linux-headers-4.10.0-35 linux-headers-4.10.0-35-generic linux-signed-image-4.10.0-35-generic"

i am looking for a way to automate this from a script, so i do not have to do it always manually. anybody knows how to solve this?

thanks in advance

K.

---

### Post by ian-weisser on 2017-10-11
Edit /etc/kernel/postinst.d/apt-auto-removal to be less conservative.

Warning: It's conservative for some very good reasons.
If you destroy your system, it's on you.

---

### Post by Doug S on 2017-10-11
There is a really cool selective kernel removal script, both a desktop and a server version, over on [askubuntu.com]("https://askubuntu.com/questions/892076/how-to-selectively-purge-old-kernels-all-at-once").

There is also a launchapd based project (but git based code. i.e. you need git to do a clone and get the script) with something very similar. [Here]("https://launchpad.net/linux-purge").

---

### Post by kerrygee on 2017-10-11
> **ian-weisser said:**
> Edit /etc/kernel/postinst.d/apt-auto-removal to be less conservative.

Warning: It's conservative for some very good reasons.
If you destroy your system, it's on you.

Hi,

thank you very much for the reply. i must confess, i really dont know where and what to modify on the script. can you give me some advice on this please.

tia

K.

---

### Post by ian-weisser on 2017-10-11
Advice: To do what you wish, you must have a good understanding of two rather basic concepts:
- How package management works
- How shell scripting works

I am uncomfortable handing you a solution for several reasons:
1) It's dangerous. You have a moderate risk of an unbootable system. Do you know how to recover from that situation?
2) You seem to lack the skills (yet) to maintain the changed script, or to fix it if the unforeseen happens. 

I do not understand why you wish to remove this basic safety precaution built into Ubuntu.

These forums are a wide community, and I am sure that others will be happy to help you understand the changes that need to be made in the script.

---

