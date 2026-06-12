---
title: "VMWare Server from Repo doesn't authenticate on Feisty Server"
date: 2007-05-19
forum: General Help
---

### Post by John64 on 2007-05-19
I have a clean installation of Feisty Fawn on my server and i installed the VMWare Server on the Canonical repository.  When i try to connect to the server in the vmware console, for any user on my machine, i get an authentication error, even though my username and password are correct.  I do not have X installed on the machine, and i would really like to keep it that way.  It seems to work in everyway other than the authentication issues

Any help is appreciated

---

### Post by veloce on 2007-05-19
> **John64 said:**
> I have a clean installation of Feisty Fawn on my server and i installed the VMWare Server on the Canonical repository.  When i try to connect to the server in the vmware console, for any user on my machine, i get an authentication error, even though my username and password are correct.  I do not have X installed on the machine, and i would really like to keep it that way.  It seems to work in everyway other than the authentication issues

Any help is appreciated

Is the version of vmware-console on your machine the same as on the server?

---

### Post by John64 on 2007-05-19
yes i am using 1.0.2, but it is the same error message if i use the 1.0.1 or 1.0.3 client.

---

### Post by veloce on 2007-05-19
> **John64 said:**
> yes i am using 1.0.2, but it is the same error message if i use the 1.0.1 or 1.0.3 client.

can you connect to the server over ssh?  That would confirm that it's a vmware issue not an authentication one.

The repositories have 1.03 now, you could try updating the server to see if that helps.

That's all I can think of, sorry I can't be more help.

---

### Post by iredden on 2007-05-19
Same problem.

Resolved it by removing /etc/pam.d/vmware-authd

it should exist in your /etc/vmware/pam.d/ directory (the one from the repo).  Hope this fixes your issue too.

---

### Post by John64 on 2007-05-20
yep, i can SSH into the box, but it is the VMWare Server Console that has issues.  I have removed that file and i am going try right now.  Nope,  i still can't log in to the server

---

### Post by veloce on 2007-05-20
> **John64 said:**
> yep, i can SSH into the box, but it is the VMWare Server Console that has issues.  I have removed that file and i am going try right now.  Nope,  i still can't log in to the server

So you are right, it is definately vmware server console causing the problem.  


Here at work I have vmware server on my local machine and we have an install similar to yours with vmware server installed on a server without X (though it is using version 1.0.1 manually installed).  

Both my system and the server have vmware-authd in both locations (/etc/vmware/pam.d and /etc/pam.d/) and they both work fine, so can't see how that would be making a difference.  I'm not sure why it has both files - maybe local users use one and remote users get the other?  The only difference in the contents is that the one in /etc/vmware/pam.d uses an environment variable %pamdir% 

You could check that the environment variable is set and that the files exist in the location specified.

---

### Post by John64 on 2007-05-20
well, using a manual installation it works fine but the manual installation would fail complaining of missing libraries.

Anyway, i removed the vmware-authd files from /etc/pam.d and /etc/vmware/pam.d and it is working well enough for me.  I didn't check the /etc/pam.d before, so i guess it was still reading that file.  What exactly is Pam? and that file

---

### Post by lawson23 on 2007-05-24
I have the same problem
[http://ubuntuforums.org/showpost.php?p=2710383&postcount=34](http://ubuntuforums.org/showpost.php?p=2710383&postcount=34)

Did anyone come to a conclusion on this?

I noticed I have both files also.
/etc/vmware/pam.d/vmware-authd
```

#%PAM-1.0
auth       sufficient       %pamdir%/pam_unix2.so shadow nullok
auth       required         %pamdir%/pam_unix_auth.so shadow nullok
account    sufficient       %pamdir%/pam_unix2.so
account    required         %pamdir%/pam_unix_acct.so

```
/etc/pam.d/vmware-authd
```

#%PAM-1.0
auth required pam_unix_auth.so shadow nullok
account required pam_unix_acct.so

```

---

### Post by harbdog on 2007-06-08
On both server and client console side, removing the "sufficient" lines in the /etc/pam.d/vmare-authd and /etc/vmware/pam.d/vmware-authd has worked for me. The only other thing my console complained of was not having execute access on a .vmx file, so chmod 777 corrected that.


phew, what a pain!

---

### Post by lawson23 on 2007-06-08
harbdog

Thank you very much for the information as I will be sure to try this out.

---

### Post by lawson23 on 2007-07-06
FYI this does not work.  Do I have to have a VMX loaded first?  If so anyone know the location it expects this?

---

### Post by lawson23 on 2007-08-07
More information,
Everything I have tried has been on the SERVER side of things and not the actual console itself.  The console is on a Windows Box not on a Linux box.  Are all these changes that everyone here has found a fix for being done where the server is or where the console is?

As I don't believe the console contains these files for Windows.

---

### Post by lawson23 on 2007-08-10
FYI a post exist in VMWARE forums concerning this without an answer.
[http://www.vmware.com/community/thread.jspa?messageID=720501&#720501](http://www.vmware.com/community/thread.jspa?messageID=720501&#720501)

---

### Post by Divan Santana on 2007-08-21
Just do the following made it work for me
cp /etc/pam.d/vmware-authd /etc/pam.d/vmware-authd.orig
vim /etc/pam.d/vmware-authd and put the following in there instead
#%PAM-1.0
auth required pam_unix_auth.so shadow nullok
account required pam_unix_acct.so

Then your unix account should authenticate

---

### Post by lawson23 on 2007-08-22
> **Divan Santana said:**
> Just do the following made it work for me
cp /etc/pam.d/vmware-authd /etc/pam.d/vmware-authd.orig
vim /etc/pam.d/vmware-authd and put the following in there instead
#%PAM-1.0
auth required pam_unix_auth.so shadow nullok
account required pam_unix_acct.so

Then your unix account should authenticate

Thank you VERY VERY much this worked like a charm!

---

