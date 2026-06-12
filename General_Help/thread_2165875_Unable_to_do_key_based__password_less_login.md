---
title: "Unable to do key based  password less login"
date: 2013-08-06
forum: General Help
---

### Post by ndnd on 2013-08-06
Hello,
I am running Ubuntu 9.10 (Server version)
I am new to linux system. I have setup SSH for password based login which is fine. However, Now I am following steps for key based login. I have generated the key pairs (Using Putty KeyGen)  on local (LOCAL) computer and sent the public key to the host computer (Server). 
I have looked at 

[HTML]
https://help.ubuntu.com/community/SSH/OpenSSH/Keys[/HTML]

On the Server=Host computer

> On the host computer, ensure that the /etc/ssh/sshd_config contains the following lines, and that they are uncommented;

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys

 



Also I have still kept password loggin on as there will users requiring password based logging while some require batch file to run. 

>   # Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes 
  

I have also restarted the service 

> sudo service ssh restart



In addition 
on the Server
I followed this exact steps 
> [dave@julia dave]$ mkdir .ssh
[dave@julia dave]$ chmod 700 .ssh
[dave@julia dave]$ cd .ssh
[dave@julia .ssh]$ touch authorized_keys
[dave@julia .ssh]$ chmod 600 authorized_keys
[dave@julia .ssh]$ cat ../identity.pub >> authorized_keys
[dave@julia .ssh]$ rm ../identity.pub


After this I simply tried to login from local computer while Putty Agent is on and the key is added (windows based SSH software - Putty).

---

### Post by ndnd on 2013-08-06
Thanks in Advance!

---

### Post by nerdtron on 2013-08-07
9.10 server? Is that still supported?

Anyway, I do it like this. From my localhost to user@serverIP, I execute the following commands.
Generate keys.
```
ssh-keygen
```
Hit enter and don't use a password. Just keep hitting enter.
```
ssh-copi-id user@serverIP
```
Enter the password for the server.
Now try logging in. It should not ask for password.
```
ssh user@serverIP
```

EDIT: Sorry I haven't read you entire post yet. You are using Putty from Windows? I don't know how to do a passwordless login using that.

---

### Post by Habitual on 2013-08-07
I believe you have to use PuttyGen to transmogrify the ssh key to a format Putty finds "acceptable".
But I could be wrong. I frequently am.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/faq.html#faq-ssh2-keyfmt](http://www.chiark.greenend.org.uk/~sgtatham/putty/faq.html#faq-ssh2-keyfmt)

---

### Post by ndnd on 2013-08-07
Hello all,
thank you for the replies. So I don't think Putty is the problem I have been able to generate the key pairs without the passphrase and also put the key public key in the .ssh folder (on server) and create authorized_keys  (on the server) as I had mentioned above. Somehow it seems the SSH restart still doesn't seem to take in the key for authentication. Which I means the server doesn't seem to have 'accepted' the key? So I feel like I am missing a step somewhere. 

How does server know where to find the public key for authentication ? Does the key being concatenated to the authorized_keys file the only requirement or do we have to run some command ?Is there a way I can verify that the server knows that this public key is there? 

Would anyone be able to mention if there is a step I am missing above I have put in as much detail as possible. ?

---

### Post by steeldriver on 2013-08-07
Take a look at your ~/.ssh/authorized_keys file - if the key you added looks like

```

---- BEGIN SSH2 PUBLIC KEY ----
Comment: "rsa-key-20130807"
AAAAB3NzaC1yc2EAAAABJQAAAIB53EZqGv0K6IfZL1yPmzB1k7iVuYN6Y4tHnIpz
On+5DYF85j7uLDmtlCbSU0pN7Q2t6CzlVcBF2y8f8LcsZ5eikORx+1aMC/xCXOPs
rdlDnLYrlbKx3EmJsZ1Ma9Dyl3eYj9i2vSeabX4xI0xvS5GGFHv8F2Au6TFkuT/f
rfB9Hw==
---- END SSH2 PUBLIC KEY ----

```

then it is in the wrong format for OpenSSH, usually meaning that you saved the PuTTY key to a file and copied that across, instead of copy-pasting the key from the area at the top of the PuTTYgen dialog box or using the 'Export OpenSSH key' option

```

Public key for pasting into OpenSSH authorized_keys file
ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAIB53EZqGv0K6IfZL1yPmzB1k7iVuYN6Y4tHnIpzOn+5DYF85j7uLDmtlCbSU0pN7Q2t6CzlVcBF2y8f8LcsZ5eikORx+1aMC/xCXOPsrdlDnLYrlbKx3EmJsZ1Ma9Dyl3eYj9i2vSeabX4xI0xvS5GGFHv8F2Au6TFkuT/frfB9Hw== rsa-key-20130807

```

Apart from that, the server knows what location to look for the authorized_keys file based on the entry in the /etc/ssh/sshd_config file:

```

AuthorizedKeysFile     %h/.ssh/authorized_keys

```

You shouldn't need to mess with the location unless you are using an encrypted home directory.

Alternatively, you can generate the key pair on the Ubuntu side using ssh-keygen (which will guarantee the key is in the correct format) and then *import *it into PuTTY on the Windows machine

---

### Post by SlugSlug on 2013-08-07
its normally
~/.ssh/authorized_keys2
not authorized_keys

Thisi is the guide I also refer to [http://paulkeck.com/ssh/](http://paulkeck.com/ssh/)

just google ssh hurly burly

---

### Post by ndnd on 2013-08-07
This worked perfectly Steeldriver. Thanks a lot!  

Based on your post now I am a bit curious so I have two questions 

1) If I add additional public key to the file authorized_keys file do I have to add to the very next line as I show below - (right onto the next line)  or do we have to add anything else? 
> ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAIB53EZqGv0K6IfZL1yPmzB1k7iVuYN6Y4tHnIpzOn+5DYF85j7uLDmtlCbSU0pN7Q2t6CzlVcBF2y8f8LcsZ5eikORx+1aMC/xCXOPsrdlDnLYrlbKx3EmJsZ1Ma9Dyl3eYj9i2vSeabX4xI0xvS5GGFHv8F2Au6TFkuT/frfB9Hw== rsa-key-20130807
ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAIB53EZqGv0K6IfZL1yPmzB1k7iVuYN6Y4tHnIpzOn+5DYF85j7uLDmtlCbSU0pN7Q2t6CzlVcBF2y8f8LcsZ5eikORx+1aMC/xCXOPsrdlDnLYrlbKx3EmJsZ1Ma9Dyl3eYj9i2vSeabX4xI0xvS5GGFHv8F2Au6TFkuT/frfB9Hw== rsa-key-20130807


I say this based on the example given on this site 

[http://wiki.mcs.anl.gov/IT/index.php/SSH_Keys:authorized_keys](http://wiki.mcs.anl.gov/IT/index.php/SSH_Keys:authorized_keys)

[HTML]An OpenSSH authorized_keys file contains a list of OpenSSH public keys, one per line. There can be no linebreaks in the middle of a key, and the only acceptable key format is OpenSSH public key format, which looks like this:

ssh-rsa AAAAB3N[... long string of characters ...]UH0= key-comment 
or

ssh-dss AAAAB3N[... long string of characters ...]UH0= key-comment 
There are slight modifications we can make to this format as outlined below, but the important pieces to know are that:

Each key is on a single line.
The key itself is the long string of characters that starts with the AAAA, and there are no spaces until the end of the key.
There are no lines that have ---- BEGIN or ---- END. If you have that in the file, you have a key of the wrong format in there.
It's perfectly acceptable to have more than one key in an authorized_keys file.
Knowing that, you can construct your keys file following the outline below.[/HTML]
======================================================

question 2
Based on your comment of generating the key pairs on the ssh system.  In this case the private key stays on the system and the public key goes out to the user?   My understanding was that 
1) each user has to generate their own key pairs wherein the private key stays on their local machine and the public key on the authorized_keys file in   [email]user@Server:~/.ssh[/email]/ folder. 
2) The Putty cannot work with the private key on the local machine developed on the Linux Server since it is installed on windows?

---

### Post by steeldriver on 2013-08-07
1) As far as I know that's correct, just append the additional keys one per line as described in the manual

2) You would copy the PRIVATE key (i.e. if you have generated an rsa keypair, copy the id_rsa file **not** the id_rsa.pub file) to the Windows machine, and then from PuTTYgen go to the 'Conversions' menu and select 'Import key' - it will recognize it as an OpenSSH private key and prompt for the passphrase if you set one. You can then press the 'Save private key' button and save the imported private key as a regular PuTTY .ppk file, which you can then add via Pagent. 

By default, PuTTY attempts to authorize via Pagent if it is running, or if you don't want to run Pagent you can point it to the .ppk file directly via the SSH -> Auth tree

---

