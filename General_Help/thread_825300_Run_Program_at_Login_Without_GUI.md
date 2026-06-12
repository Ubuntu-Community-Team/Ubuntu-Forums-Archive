---
title: "Run Program at Login Without GUI"
date: 2008-06-10
forum: General Help
---

### Post by MDSmith2 on 2008-06-10
Hello.
I want to know how i can run a command at login (psql to be exact).
I'm not using the gui for performance.

---

### Post by sdennie on 2008-06-10
You should be able to create a file called ~/.profile and add commands to it.  If they are things you don't want started for every login shell, you'd have to check to see if the thing is already running before starting it though.

Edit:
Was thinking tcsh.  The correct file is ~/.profile in bash I think.

---

### Post by PsYvEnOn on 2008-09-26
> **vor said:**
> You should be able to create a file called ~/.profile and add commands to it.  If they are things you don't want started for every login shell, you'd have to check to see if the thing is already running before starting it though.

Edit:
Was thinking tcsh.  The correct file is ~/.profile in bash I think.


I didn't understood very well! I'm trying to run VMware at login without GUI and i can't solve the problem! Can you be more specific?


regards

---

### Post by kpkeerthi on 2008-09-26
--pls disregard--

---

### Post by Peter09 on 2008-09-26
To run a program without logging in use the /etc/rc.local script. This is run at boot time. However remember that the 'default' user who runs the command is root and the default 'home' directory is /.

*Perhaps I misread your requirement there, I think you do want to login before running it...if so ignore above*

---

### Post by PsYvEnOn on 2008-09-26
> **Peter09 said:**
> To run a program without logging in use the /etc/rc.local script. This is run at boot time. However remember that the 'default' user who runs the command is root and the default 'home' directory is /.

*Perhaps I misread your requirement there, I think you do want to login before running it...if so ignore above*

First of all, thanks for helping!

If i do your way, how can i login in my system when i want to? If that script runs the program before the login screen, how can i login later?
In fact, i want to run a program after login and get sure that the user that logged cannot exit the program (security measures). If user exit the program, it should logoff.

Is it possible?

---

### Post by Peter09 on 2008-09-26
Well Ubuntu is a multiuser system, it will support many users logging in at the same time. So you would just login as normal, the program that you run from rc.local would be running somewhere on your system, but unless you looked for it you would not know.

I think any user that is not an 'admin' user will not be able to leave programs running once they have logged out.

---

### Post by Peter09 on 2008-09-26
I am unsure of your requirements. If you are saying that the user should log into a virtual machine, then you are asking the wrong questions. Do you want vmware to run a virtual machine which users log into?

---

### Post by PsYvEnOn on 2008-09-26
> **Peter09 said:**
> I am unsure of your requirements. If you are saying that the user should log into a virtual machine, then you are asking the wrong questions. Do you want vmware to run a virtual machine which users log into?

I'll try to be more specific.

I want that when a certain user do the login, vmware starts automatically and the user that logged in can only work with vmware program. It is supposed that when the user finish to work with vmware, the log off is immediately done! This is to ensure that the user only works with vmware and cannot access the desktop for example!

Did i make myself understood?

Sorry if my english is bad! :lolflag:

---

### Post by Peter09 on 2008-09-26
Yes, but I think you may misunderstand how VMWARE works. Lets say the machine you have at present is called PHY for the physical machine. You will configure VMWARE to run a machine called VIRT for a virtual machine.

When you log into your physical machine (PHY) you will see a tasks running called VMWARE (or similar) which looks just like other tasks on your system. There will be no interaction. You will see the PHY systems' files etc.

However if you look on the network you will see two machines running (PHY and VIRT). If set up properly the VIRT machine will have a different IP address to the PHY machine. Your user will remotely login to the VIRT machine across the network. To him he is logged into a real machine and sees only that machines filesystem etc and any shares that are configured. He does not see the PHY machine at all.

That would be the normal way of using a virtual machine to isolate users from the server.

On the PHY machine, if you were logged in you would see no difference, except the VMWARE task would be taking more CPU and resources than when it was idle.

Does this clarify it? Is this what you want to do?

---

### Post by PsYvEnOn on 2008-09-26
I think it will be fine! So, how can i log into the Virt by network?

---

### Post by Peter09 on 2008-09-26
There are several ways to do that, from FREEnx, x11vnc, ssh, etc. The first thing is to get VMWARE running as needed. I have never used VMWARE, I use a product called VirtualBox, which is in the repositories as well. I find it easier (I am sure others would go for VMWARE).

So I can help you with VirtualBox but not VMWARE. I am sure there are others who can though.

---

### Post by PsYvEnOn on 2008-09-26
> **Peter09 said:**
> There are several ways to do that, from FREEnx, x11vnc, ssh, etc. The first thing is to get VMWARE running as needed. I have never used VMWARE, I use a product called VirtualBox, which is in the repositories as well. I find it easier (I am sure others would go for VMWARE).

So I can help you with VirtualBox but not VMWARE. I am sure there are others who can though.

Thanks a lot for your precious help Peter09 :)

---

