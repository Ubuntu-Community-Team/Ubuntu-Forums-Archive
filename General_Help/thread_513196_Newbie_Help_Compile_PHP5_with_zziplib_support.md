---
title: "Newbie Help: Compile PHP5 with zziplib support"
date: 2007-07-30
forum: General Help
---

### Post by psykro on 2007-07-30
I could use some help in compiling php with zip support.

I have searched the forum and the net to find out the answers to this.

So far I have discovered the I need to "apt-get install zziplib-bin" to install the zziplib app (which I have done) and then I have to run './configure' '--enable-zip' to enable zip support. 

What I don't know and can't find is where I have to run this command? I assume I have to be in the php application folder but I don't know which folder that is. (wouldn't even know where to start looking)

The server is kubuntu 6.06 LTS and I only have command line (putty) access. 

Thanks in advance for any assistance.

---

### Post by dreadlord_chris on 2007-07-30
> **psykro said:**
> I could use some help in compiling php with zip support.

I have searched the forum and the net to find out the answers to this.

So far I have discovered the I need to "apt-get install zziplib-bin" to install the zziplib app (which I have done) and then I have to run './configure' '--enable-zip' to enable zip support. 

What I don't know and can't find is where I have to run this command? I assume I have to be in the php application folder but I don't know which folder that is. (wouldn't even know where to start looking)

The server is kubuntu 6.06 LTS and I only have command line (putty) access. 

Thanks in advance for any assistance.

You would run the command, before compiling PHP, from the folder that you have the **source code for PHP** in.

---

### Post by psykro on 2007-07-30
So can I not recompile the current version of PHP that is installed on the machine to add the zip support ?

---

### Post by digen on 2007-07-30
First, is the current installed of PHP via source or have you installed it using APT/Synaptic ? 

If it was via the package manager, then you'll need to download the PHP 5 source tar ball, extract it and execute the ./configure script with the various command line options like Zlib etc and then 'make' and 'make install'.

You could also separate the installations by defining the PHP installation via source using the '--prefix=/path/to/where/php/will/be/installed/'

---

### Post by psykro on 2007-08-01
Thanks for the tips. I will try those steps. Just one more question, is there a way I can view the current configuration file to ensure that the new compiled version of php has the same settings as the current one, I don't want to break anything.

---

