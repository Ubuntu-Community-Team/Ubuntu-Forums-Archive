---
title: "web content filtering/parental controls"
date: 2008-02-05
forum: General Help
---

### Post by &amp;)ky#)^ on 2008-02-05
I've got a friend whose young teenage son wants to switch to Ubuntu.  Great for him.  However, my friend believes in the use of web content filters to protect her children, all of whom are the son's age or younger, from whatever.  I'd like to help her set that up in Ubuntu if it's possible.

Here's the catch, though.  I think the son's user account should have permissions to install new software on the computer.  However, that account shouldn't be able to modify or disable the content filtering program.  Is such a thing possible?  Last I checked, you're either root or you're not, at least when it comes to installing packages.

Assuming such a setup was possible, how could it be done and what content filtering software is recommended?  I also figured that my friend and her husband could somewhat easily modify what is filtered while the blacklist updates could be handled automatically by cron.

What do you think?  Possible?

---

### Post by stalker145 on 2008-02-06
> **bluej774 said:**
> I've got a friend whose young teenage son wants to switch to Ubuntu.  Great for him.  However, my friend believes in the use of web content filters to protect her children, all of whom are the son's age or younger, from whatever.  I'd like to help her set that up in Ubuntu if it's possible.

Here's the catch, though.  I think the son's user account should have permissions to install new software on the computer.  However, that account shouldn't be able to modify or disable the content filtering program.  Is such a thing possible?  Last I checked, you're either root or you're not, at least when it comes to installing packages.

Assuming such a setup was possible, how could it be done and what content filtering software is recommended?  I also figured that my friend and her husband could somewhat easily modify what is filtered while the blacklist updates could be handled automatically by cron.

What do you think?  Possible?

For filtering, personally, I use [OpenDNS]("http://www.opendns.com/"). I set all the computers on the network with DHCP, set the router to default to OpenDNS's DNS servers, do some quick clicking in the OpenDNS preferences, and enjoy. They update everything on their own, you can specify the level of "maturity", you can white/black list web sites. 

Oh, and it's free :D

---

### Post by &amp;)ky#)^ on 2008-02-07
I like where you're going with that.  Sounds good to me.  Just take the selected blacklists from where ever and apply them to opendns.

The only problem is that there is no network.  This is the one family computer.  Plus, the son should have access to install software (which requires root) but not to edit settings to choose a different dns server if you were using opendns.  Any ideas for that little kink?

---

### Post by sloggerkhan on 2008-02-07
I don't think you can give him reasonable install/admin permissions and expect packages to work properly unless the filtering is done upstream. 
While there can be a very high level of customization in what's allowed with privilege escalation, a lot of installs will need access that I am fairly certain could be used to circumvent any filters. 

Just my opinion. I'm not that knowledgeable, though, so I look forward to seeing some more responses.

Hate to comment here on this, but once you've got a teenager, you probably need to start trusting them at some point so far as technology goes.

---

### Post by kesman on 2008-02-07
Maybe you should tell your friend to have a chat with the teenager about the stuff he might run into when surfing. No filter is good enough to 100% protect him about the bad stuff, so he'll run into it eventually.

---

### Post by &amp;)ky#)^ on 2008-02-07
You're right.  I don't believe in such things as internet censorship.  However, it's my friend's viewpoint that she believes in using it to keep her children from porn and such.  It's not my place to contest her viewpoint for her kids.  I'm not a parent.  What does matter is that her son is very smart and wants to use Ubuntu.  I think it would be a wonderful thing for him to continue learning about linux and open source software via experiencing and exploring Ubuntu.  The only way that's going to happen is if I can figure out a way to allow for some filtering to be possible.  At the same time, I think the kid should be able to install some software without having to ask his mom.  I only say this because I know how often I install and uninstall software.

OpenDNS sounds the most promising thus far.  The only problem is that I'm in Chicago and there are no local servers yet.  I don't want to slow down the internet just to filter it.

---

### Post by kesman on 2008-02-07
[http://ubuntuforums.org/showthread.php?t=177591](http://ubuntuforums.org/showthread.php?t=177591)
There's a lot of disussion about this. I agree to them that preventing something from sudo user is quite impossible, but maybe there's still something to do about it.

---

### Post by &amp;)ky#)^ on 2008-02-07
Just to keep this thread updated, I've decided to recommend the use of OpenDNS.  Thanks Stalker145 for the tip.

Now, the only obstacle is to block editing of the /etc/resolv.conf file and block editing AND viewing of a cron shell script I wrote to update a dynamic ip to the OpenDNS website.  The latter file must be blocked due to a plaintext password that the kids shouldn't know.

Shouldn't editing the sudoers file properly do the trick?  Oh, and either /etc/sudoers or the visudo command should be blocked to disallow editing of the sudoers file.

---

