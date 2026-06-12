---
title: "VMWare Server and AMD Dual Core"
date: 2007-05-09
forum: General Help
---

### Post by kprowell on 2007-05-09
I've been checking the forums both here and at vmware about the issue I am having trying to get vmware server running.  I finally got it installed via Synaptic now that it is in the commercial repos.  The install went well.  I can create a VM but when I try to boot the VM that's when it fails.  I thought I read somewhere about issues with AMD (or Intel) dual core processors but I can't find anything concrete (not that it doesn't exist).  Has anyone had this problem and found a way to fix it?

My machine specs are:

AMD Athlon 64 X2 3800
2GB Ram
250GB SATA HDD
NVIDIA 7300 256MB PCIE Video
and misc USB and Firewire, etc.

FYI.  This machine used to be a AMD Athlon 64 single core at one time and it worked then.  I am able to install and run VMWare on my XP partition as to rule out hardware issues.  Any help with this would be greatly appreciated! :)

---

### Post by seamuso on 2007-05-09
I haven't had any issues with vmware installed on a dual core system.

[quote=kprowell]The install went well. I can create a VM but when I try to boot the VM that's when it fails.[/quote]

What do you mean by fails? I saw that you used the repositories for the install, but have you tried removing that install and using the install files directly from vmware (how I have always installed).

Here's the howto for the install ..  

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

Hope this helps.

---

### Post by kprowell on 2007-05-09
Actually, that's how I tried it before with the same result.  Once I heard that it was in the repos, I tried installing it that way hoping it would work but it didn't.  What happens is, I can create the VM but when I start the Vm it just instantly shuts down.  Every so ofter I get a message box that tells me to start with debugging enabled and then look at the logs.  I did that and I have the log file.  I can't tell from it what's causing it to instantly crash.

---

### Post by seamuso on 2007-05-09
Try running it from a terminal window so you can see all the output. When it fails, it may spit the specific error out .. also, when you installed/reinstalled, did you remove the /etc/vmware dir so you weren't picking up any previous configs?

---

### Post by kprowell on 2007-05-09
Can I actually start the virtual machine from the cli?  Because Vmware starts just fine, it's just that the virtual machine(s) won't.  Also, yes, I deleted everything before I reinstalled.  Now, the only thing I can think of trying is backup my /home directory and reinstall Ubutnu 7.04 since this machine was running alpha's and upgraded to the official release through Update Manager.  Thoughts?

---

### Post by seamuso on 2007-05-09
Are you running 32bit or 64bit feisty?

You can't start the specific vm from a terminal, but you can start vmware itself to errors it may be starting with .. for instance```
# vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

```

happens, but you don't know unless you run it from a terminal (not an issue that causes your problem).

Here's a more detailed example from the vmware forums -

[quote=From VMWare forums]# vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: File "/etc/vmware/config" line 18: Variable `vix.libdir' is already defined.



VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: File "/etc/vmware/config" line 18: Variable `vix.libdir' is already defined.

A log file is available in "/tmp/vmware-root/ui-26948.log". Please request support and include the contents of the log file.
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.
[/quote]

Again, you won't see these errors unless you start from a terminal

---

### Post by kprowell on 2007-05-09
I'm running 32bit Feisty.  Again, I can always try a fresh install since this install was from the Alpha version of Feisty with all it's updates.  It actually never gave me the option to Officially upgrade when 7.04 final was released so maybe there's a problem with the install.  Just guessing...

---

### Post by kprowell on 2007-05-09
I did a clean install of Feisty and then VMware.  All went well.....again.  I ran vmware and created a vm (XP).  When I hit start here's what I get...

*** VMware Server internal monitor error ***
vcpu-0:VMM fault: regs=0x2f24, exc=7, eip=0x452df
Please report this problem by selecting menu item Help > VMware on the Web > Request Support, or by going to the Web page "http://www.vmware.com/info?id=8&logFile=%2Fvar%2Flib%2Fvmware%2Dserver%2FVirtual%20Machines%2FWindows%20XP%20Professional%2Fvmware%2Elog&coreLocation=%2Fvar%2Flib%2Fvmware%2Dserver%2FVirtual%20Machines%2FWindows%20XP%20Professional%2Fvmware%2Dcore%2Egz". Please provide us with the log file (/var/lib/vmware-server/Virtual Machines/Windows XP Professional/vmware.log) and the core file (/var/lib/vmware-server/Virtual Machines/Windows XP Professional/vmware-core.gz).
If the problem is repeatable, please set 'Logging level' to 'Debug' in the Misc panel of Virtual Machine Settings. Then reproduce the incident and file it according to the instructions.
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.
We appreciate your feedback,
  -- the VMware Server team.

---

### Post by etew on 2007-06-16
Hello
I have exactly the same problem, whatever the way I installed vmware, whatever the way I launch it. I tried  to launch vmware from a console, but I couldn't see any particular message.
My computer is a laptop NX6325 (AMD Turion 64x2).

Did you find a solution since your post?

---

### Post by kprowell on 2007-06-17
No, not at all.  I've tried so many things and still nothing.  I even opened up a ticket with VMWare but they never got back to me.  I've tried Parallels and VirtualBox too.  They all fail.  The only thing I have not tried is a different distro.  Everything works fine under Windows XP.  If you haven't tried other apps for virtualization, I suggest giving them a try.  Let me know how it goes.

---

### Post by Ocxic on 2007-06-17
when you creat the vurtual disk, it asks to split the file into 2 gb chunks try not doin that, I fond it give better performance anyway.

---

