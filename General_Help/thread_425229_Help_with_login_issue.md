---
title: "Help with login issue"
date: 2007-04-27
forum: General Help
---

### Post by roffy on 2007-04-27
Alright, I have just really been getting into linux other than the slight dabbling I have done in the past. So take it easy on me.

I am using Ubuntu and I recently gave my user account root access/powers. I know that is discouraged but I wanted to do it anyway. Well, me being a n00b, didn't even think about how it wouldn't let me login to GDM using my name after receiving those powers. So now I can't log in. When I try to create a new user I am able to but an error pops up every time I try to log in with that user that say something like 

"User $HOME/.dmrc file is being ignored...." 

I just want to know 

A. Is there a way I can log in with root or
B. Is there a way I can make it so my user doesn't have root powers anymore or
C. Is there a way I can get a new user working properly so I can fix my other problems

Thanks in advance

---

### Post by binarybird on 2007-04-27
roffy...there is a way you can log in to your system as root, but you are not going to use the GUI. 

When you boot into the box you are usually presented with a few options from GRUB. One of these options is to boot into "Recovery" mode or what is called "single user" mode. This will boot the kernel and drop you to just a plain root console. 

You're description of what you did exactly to promote your account to root was vague so to be on the safe side I would go ahead and delete the entire account while in single user.

# userdel <account name>
# rm -Rvf /home/<account name>

Then create yourself a new account:

# adduser <new account name>

and follow the prompts. It should end up looking something like this:
Adding user `someaccountname' ...
Adding new group `someaccountname' (1002) ...
Adding new user `someaccountname' (1001) with group `someaccountname' ...
Creating home directory `/home/someaccountname' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for someaccountname
Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [y/N] y

Once you've done that reboot the box

# shutdown now -r

You can then log in using your new account. 

since you're a noob I applaud your willingness to get your hands dirty but remember good habit to form now is only use root for what you need. It's much easier and safer to just "sudo" when you need to run as root, or become root temporarily "su" to accomplish specific tasks. 

Unlike Windoze you still have pretty wide latitude in Linux as a regular user. 

Hope that helped! Happy computing.......

---

### Post by Hendrixski on 2007-04-27
Yeah, I'm just going to reiterate the point of NOT running your computer as root.  It's a security thing.  Because if you run as a regular old account and you accidentally do something bad (like rm -r  *.*) or if you download a malicious program (of which there aren't many) or if some hacker compromises your computer, then they can only mess up your account.  Nothing else.  I you're root, then you can mess up the entire system.

So yeah, good habits are there for a reason.

Like the other guy said, you're not allowed to do GUI stuff as Root (because that is SUPER unsafe), so you'll have to log in in safe mode, where you can log in as root, and add the user account manually (like in the old days when men were men and wrote their own device drivers).

But most importantly.  WELCOME to the community.  If you have any questions feel free to ask.  :-) 
Enjoy Ubuntu, and we look forward to seeing you around more.  Check out your local Ubuntu chapters (Ubuntu loco teams) and see if there aren't any fun projects you would like to get involved with.  The sky is the limit.  :-)

---

### Post by roffy on 2007-04-27
Thats guys, that worked for me. And I will follow your advice and not try doing that again.

---

