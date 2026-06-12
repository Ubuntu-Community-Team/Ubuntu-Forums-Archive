---
title: "ssh username@server-bash: /usr/bin/awk: cannot execute binary file: Exec format error"
date: 2020-03-19
forum: General Help
---

### Post by killowattyone on 2020-03-19
Hi.
   
  I’ve searched the forum and the web, but failed to find an answer to this ssh issue. Currently running Ubuntu 19.10 eoan, ssh: OpenSSH_7.4 OpenSSL 1.0.2u. When using autocomplete with ssh (press tab to auto fill a server name from /etc/hosts), bash reports the following error:

  ssh -bash: /usr/bin/awk: cannot execute binary file: Exec format error
   
  This occurs on one specific server, all others autocomplete fine with a variety of distros and os-versions. Any ideas? 
   
  Cheers.
   
  Ken

---

### Post by TheFu on 2020-03-19
The correct format of the command don't have ':'

```
$ ssh username@server-bash /usr/bin/awk
```

Or better, setup a ~/.ssh/config file so you don't need the username@ part.

I'm assuming you aren't really trying to run awk.  What, exactly, is the ssh command being used?

---

### Post by killowattyone on 2020-03-19
Thefu,

Tx for the quick reply. I should've made it clearer in my query:

1. Command entered: ssh username@serveraddress (or name)
2. Tab for server address autocomplete works perfectly on the rest on my servers 
2. On the server with this issue, pressing tab to autocomplete the server address autocomplete, bash reports: -bash: /usr/bin/awk: cannot execute binary file: Exec format error
3. I am not trying to run awk.

I'll look into creating the ssh config as suggested. 

Cheers

Ken

---

### Post by TheFu on 2020-03-19
Please show the exact command + exact outpout and use code tags to things look ***100%, exactly***  like they do in the terminal.

Here, I had to follow a few symlinks to find the real awk being used:
```
tf@hadar:~/V$ file /usr/bin/awk
/usr/bin/awk: symbolic link to /etc/alternatives/awk
tf@hadar:~/V$ file /etc/alternatives/awk
/etc/alternatives/awk: symbolic link to /usr/bin/gawk
tf@hadar:~/V$ file /usr/bin/gawk
/usr/bin/gawk: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/l, for GNU/Linux 2.6.32, BuildID[sha1]=38028e7fa7d204e30764568640ead5bb665aa125, stripped
```
The system is an x86-64 ELF machine.

On an ARM machine, 
```
osmc@pi3:~$ ls -al /usr/bin/awk
lrwxrwxrwx 1 root root 21 Dec 31  1969 /usr/bin/awk -> /etc/alternatives/awk
osmc@pi3:~$ ls -al /etc/alternatives/awk
lrwxrwxrwx 1 root root 13 Feb 18 13:13 /etc/alternatives/awk -> /usr/bin/gawk
osmc@pi3:~$ ls -al /usr/bin/gawk
-rwxr-xr-x 1 root root 446640 Jan 25  2017 /usr/bin/gawk
```

---

### Post by killowattyone on 2020-03-19
The desired login server is named bittorrentserver. The exact command starts with:

ssh pi@bit + Press tab key for autocomplete.

bash immediately appends the above with -bash: /usr/bin/awk: cannot execute binary file: Exec format error. So, in other words, after pressing the tab key, the command looks like: 

ssh pi@bit-bash: /usr/bin/awk: cannot execute binary file: Exec format error
-bash: /usr/bin/awk: cannot execute binary file: Exec format error
torrentserver

Note: If I press enter at this point, bittorrentserver prompts for authentication.

awk (ARM machine)

xx@Sandbox:~ $ ls -al /usr/bin/awk
lrwxrwxrwx 1 root 0 21 Oct  9  2018 /usr/bin/awk -> /etc/alternatives/awk

xx@Sandbox:~ $ ls -al /etc/alternatives/awk
lrwxrwxrwx 1 root 0 13 Jan 13 16:06 /etc/alternatives/awk -> /usr/bin/gawk

xx@Sandbox:~ $ ls -al /usr/bin/gawk
-rwxr-xr-x 1 root 0 544880 Jan 25  2017 /usr/bin/gawk

---

### Post by TheFu on 2020-03-19
Try running: /usr/bin/gawk
Does that work?

if not, try reinstalling the gawk/awk package?
Bash has a command completion package where scripts magically perform the completions.  Might try reinstalling that package too.

if you just want something that works, now, today, add the 'bit' hostname to your local /etc/hosts for the other machine 
or
setup a ~/.ssh/config file so you don't need bash-completion. 
Ref first comment here: [https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

---

### Post by killowattyone on 2020-03-20
Thank you for your perseverance. The issue clearly lies with the relationship between ssh and the tab completion function. I have found an interim solution at Andy Lester's Blog: [https://blog.petdance.com/2019/10/31/tab-completion-for-ssh-scp/](https://blog.petdance.com/2019/10/31/tab-completion-for-ssh-scp/)  (October 2019). Since only one server is affected, I will explore the complete command list, and look for differences there (i.e missing scripts etc).

---

### Post by killowattyone on 2020-03-21
The following fixed the issue: 

sudo update-alternatives --config awk

Selected mawk from the alternatives list. ssh now works with tab completion as as expected.

---

