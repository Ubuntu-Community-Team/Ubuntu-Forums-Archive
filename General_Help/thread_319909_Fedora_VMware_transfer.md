---
title: "Fedora VMware transfer"
date: 2006-12-16
forum: General Help
---

### Post by treasonx on 2006-12-16
I have recently switched from FC6 to ubuntu. So far so good, except for one problem.

When I try to start a virtual machine on ubuntu that I use to use on my Fedora installation. I get the following error.

```

Unable to change virtual machine power state: Couldn't determine owner of config file /netDisk/James/vmware/DVD/New Install Windows XP Professional.vmx
Check that a line for uid 500 appears in /etc/passwd.

```

Any ideas?? 

Thanks

---

### Post by gaebriel on 2006-12-16
UID 500 is the default UID assigned to the first user you create on Fedora/RedHat. Ubuntu, Suse, and others perhaps use 1000. The problem you're running into is permissions related and since UID 500 doesn't exist in the default install of ubuntu, you can just fix things by taking ownership of the files you're trying to modify. Try running: 

```
chown YOUR-USER.YOUR-GROUP /netDisk/James/vmware/DVD/New Install Windows XP Professional.vmx
```

or 

```
sudo chown YOUR-USER.YOUR-GROUP /netDisk/James/vmware/DVD/New Install Windows XP Professional.vmx
```

You'll probably want to change ownership on all the files in that directory so you can write to them as well. You can do that by running: 

```
sudo chown YOUR-USER.YOUR-GROUP /netDisk/James/vmware/DVD/* -R
```

HTH, Enjoy!

P.S. If you run `id` from a terminal, it'll list all the UIDs associated with your account. Replace the "YOUR-USER" and "YOUR-GROUP" with the values from `id`.

---

### Post by treasonx on 2006-12-16
That fixed one error.. Thanks :) 

Now i get this one. Any ideas?

```

Unable to change virtual machine power state: The process exited with an error:
End of error message.

```

---

### Post by gaebriel on 2006-12-21
What do the vmware logs (/tmp/vmware-USERNAME/*.log) say? I googled for your error and found this link which makes me think it may still be a permissions issue: [http://www.vmware.com/community/message.jspa?messageID=443280]("http://www.vmware.com/community/message.jspa?messageID=443280")

---

### Post by stormzen on 2008-03-30
Running CentOS5, I encountered the same problem.  It happened because I had to manually change the UIDs in the /etc/passwd file on the file server (CentOS) when I installed Ubuntu as a client (and it started with UID 1000 instead of 500).  Made a horrible mess on the file server, but I'm still not sure that there was a way around it because there was a Good Reason that Ubuntu started with 1000 (if memory serves.)

In any case, I was about ready to quit my job when the VM that held the company's Quickbooks wouldn't come up, first for the the error:
```

Unable to change virtual machine power state: Couldn't determine owner of config file (blah)
Check that a line for uid 500 appears in /etc/passwd.

```

and then after I renamed the obvious files, I got the much more cryptic error:
```

Unable to change virtual machine power state: The process exited with an error:
End of error message.

```

It was turning out to be a bad night for me.  Until I found some log files in /tmp/vmware-jae that complained thusly:
```

Mar 30 00:26:03: vmx| Log for VMware Server pid=6168 version=1.0.4 build=build-56528 option=Release
Mar 30 00:26:03: vmx| Command line: "/usr/lib/vmware/bin/vmware-vmx" "-C" "-@" """" "/home/temp-qb/VirtualQB/VirtualQB.vmx"
Mar 30 00:26:03: vmx| CnxCreateUserProtectedDir: File "/var/run/vmware/jae" has attributes that are incompatible with this application. Please delete or rename the file.
Mar 30 00:26:03: vmx| Cnx_CreateSocketDir: Failed to create user socket dir.
Mar 30 00:26:03: vmx| VMXVmdb_Init Failed: ret = VMDB failure
Mar 30 00:26:03: vmx| Failed to initialize the VMX VMDB instance

```

So I deleted these files:
```

drwx------ 2  500  500 4.0K Mar 29 23:49 jae
lrwxrwxrwx 1 root  500   24 Jan 18 22:57 %2Fhome%2Ftemp%2Dqb%2FVirtualQB%2FVirtualQB%2Evmx -> /var/run/vmware/jae/9903

```

( Note that the second entry links to a file in the path I just deleted in the first entry. )

Then all was right with the world again.

---

