---
title: "[SOLVED] Update Manager hangs, Synaptic Package Manager won't start"
date: 2008-06-14
forum: General Help
---

### Post by L a r r y on 2008-06-14
Dear Friends,
I have 50 updates available, in Ubuntu 8.04, and after I click the icon and choose to install, the Update Manager window becomes unresponsive.  No matter how many mouse clicks I run on the corner X to close the window, or how many times I use the close menu item from the task bar, it does not respond.  I did not try to minimize the window, but I can switch to the other workspace and I can run other programs, and access the menu system.

If I power down, restart or log off and back on again, the desktop comes up and I am advised that I have these 50 updates available.  I clicked the icon and removed most of the updates, leaving the two security updates and tried to install those, but again the manager just sits there.

In my forum research, I found a poster who tried to use add/remove to remove the Update Manager and was advised to use the Synaptic Package Manager instead.  So I tried the add/remove and was given the same advice, went into administration and tried to start the Synaptic Package Manager and it won't start.

How do I go about repairing things?

I ran a few Perl scripts in my Terminal from an online Perl tutorial, using the perl -e  and all went well with that before I ran one asking me to enter my email address and it evaluated whether what I put in looked like an email address or not.

It **was supposed to** prompt me with:  "So what's your email address, anyway?" and one of its responses was "Say, who do you think you're kidding?"

```
perl -e '
# some code
print "So what's your email address, anyway?\n";
$email=<>;
# some more code
'
```
I discovered that the apostrophe in the word "what's" and the one in "you're" were the stumbling blocks because the first one of these encountered was taken to be the ending single quote delimiter.  The code was listed on the Terminal, leaving me in the > prompt.  Ordinarily, the script is listed and then executed, leaving me in the $ prompt when it finishes.

I have learned that ctrl-c will exit this > prompt.

I don't know if this instance of experimentation was the culprit to throw my updates into a tarball, but I did this since my last successful update.

(Solution to my Perl script running instead of hanging was to replace the apostrophe in the two words in the print statements with the ` symbol under the tilde to the left of the number 1 key.)

Thank you for your help!

---

### Post by L a r r y on 2008-06-14
Anyone have any suggestions on a recovery?

---

### Post by kalesh7 on 2008-06-14
I don't think perl scripts could do anything that drastic
see if upgrading from command line works?
```
sudo apt-get update
sudo apt-get upgrade

```
this should upgrade all your packages(or show you some errors which can help at getting at the update manager problem)

---

### Post by cariboo on 2008-06-15
Check you /etc/hosts file to see if you have something like this:

```
127.0.1.1	intrepid
```

Where intrepid is replaced with your hostname with no extras.

Jim

---

### Post by L a r r y on 2008-06-15
> **kalesh7 said:**
> 
see if upgrading from command line works?
```
sudo apt-get update
sudo apt-get upgrade

```
this should upgrade all your packages(or show you some errors which can help at getting at the update manager problem)
Indeed it did accomplish the upgrade.  First command requested my password and then listed all the updates available, and then second command was issued to perform the upgrade.

In both instances, Sudo could not resolve my domain, which I had recently changed from a long name to a short one.  I had not been able to figure that out, but in Jim's post (which I tried to include in a multi-quote without success), he pointed me to my hosts file, and ip address of 127.0.1.1.  There was my old domain name.

Used [COLOR="DarkRed"]gksudo gedit /etc/hosts[/COLOR] in the alt-F2 dialog, but it would not start, so I opened the Terminal and 
ran **[COLOR="DarkRed"]sudo gedit /etc/hosts[/COLOR]** in Terminal to change the hosts entry to my current short name.

Now I can open the Synaptic Package Manager, and my system is up-to-date.  Thanks to both of you for your help, and I can mark this thread as solved.:)

---

### Post by L a r r y on 2008-06-15
> **kalesh7 said:**
> I don't think perl scripts could do anything that drastic
see if upgrading from command line works?
```
sudo apt-get update
sudo apt-get upgrade

```
this should upgrade all your packages(or show you some errors which can help at getting at the update manager problem)

> **cariboo907 said:**
> Check you /etc/hosts file to see if you have something like this:

```
127.0.1.1	intrepid
```

Where intrepid is replaced with your hostname with no extras.

Jim

Now I see how it is done to multi-quote from more than one post:
Mark each post that you want to quote from** with the multi-quote button**, then select the last one with the Quote button.

Both of these posters gave me the correct information to solve this thread.  Thank you!

---

### Post by dinofizz on 2008-10-15
I had the same problem, and after following the suggestions from this thread was able to solve it by editing my hosts file. I would like to know WHY changing the hosts file solves the problem.

The problem appeared after I was playing around with samba in accessing a windows pc on my network. my hosts file had the line

```
127.0.1.1 <hostname>.mshome
```

mshome is the workgroup I was using for accessing the windows shared folder.

Removing the .mshome solved the problem, but where did it come from and why was it in this file?

---

