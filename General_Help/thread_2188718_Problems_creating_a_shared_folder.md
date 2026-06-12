---
title: "Problems creating a shared folder"
date: 2013-11-18
forum: General Help
---

### Post by jweaver682 on 2013-11-18
Hi, I have an Ubuntu machine that is a few years old that I would like to turn into just a simple file server that I can access from my Windows 7 machine. I created a folder and set it so it could be edited and shared with other computers but my Windows machine still can't see it in the network. I would be grateful if anyone could help me with this.

---

### Post by TheFu on 2013-11-18
[https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html) is what you need.

---

### Post by drmrgd on 2013-11-18
Windows can't see it because it doesn't know to read Linux file systems by default.  Probably the easiest way is to create a samba share, which Windows can see.  Here's a link to some pretty decent instructions for setting this up:

[Setting up a Samba Share in Ubuntu]("https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way")

And here's an older, but fairly decent video tutorial for how to do this.  My only argument is that the person in the video chose to put the shared folder in root, and I'd probably prefer to put that in $HOME or /media.  Just personal preference, though :)

[Setting up Samba Share Vid]("http://www.youtube.com/watch?v=p2r0kIB_ItE")

EDIT: Dang!  Got Kung Fu'd by TheFu!  I type too slowly!

---

### Post by jweaver682 on 2013-11-18
Thanks a lot, that really helped. I have my shared folder up and running. The only problem is that it doesn't appear under network locations, but it is still accessible through the server's IP address. Still, it works. Thanks a lot.

---

### Post by TheFu on 2013-11-18
Do you have DNS or /etc/hosts (or the windows equiv) setup?  That's the only way to avoid the IP access. Then I think the nmbd service can broadcast the hostname in a way that Windows understands.

---

### Post by jweaver682 on 2013-11-18
> **TheFu said:**
> Do you have DNS or /etc/hosts (or the windows equiv) setup?  That's the only way to avoid the IP access. Then I think the nmbd service can broadcast the hostname in a way that Windows understands.

I actually think I do have DNS hosts set up. I'm going to lie I am clueless when it comes to networking, and am not going to pretend I know what that means, I just seem to recall seeing the DNS numbers when configuring my router for the first time.

---

### Post by bab1 on 2013-11-18
> **TheFu said:**
> Do you have DNS or /etc/hosts (or the windows equiv) setup?  That's the only way to avoid the IP access. Then I think the nmbd service can broadcast the hostname in a way that Windows understands.

By default Samba converts the hostname (via /etc/hosts) to a NETBIOS name which Windows understands.  The easiest way to set the NETBIOS name on a Samba server is to add a line to the smb.conf like this:```
netbios name <some name>
```...where <somename> is a name of your choice no longer than 15 characters.  I match the NETBIOS name to my hostname but you don't have to.

---

### Post by bab1 on 2013-11-18
> **jweaver682 said:**
> I actually think I do have DNS hosts set up. I'm going to lie I am clueless when it comes to networking, and am not going to pretend I know what that means, I just seem to recall seeing the DNS numbers when configuring my router for the first time.

This must be in the /etc/hosts file.  That's what the Samba server daemon named *nmbd* checks to convert to a NETBIOS name.  The nmbd daemon does not look for DNS served names per se, only /etc/hosts mapped names.  But like I said in the previous post you can bypass all of that by explicitly defining the NETBIOS name in the smb.conf file.

---

### Post by jweaver682 on 2013-11-18
> **bab1 said:**
> By default Samba converts the hostname (via /etc/hosts) to a NETBIOS name which Windows understands.  The easiest way to set the NETBIOS name on a Samba server is to add a line to the smb.conf like this:```
netbios name <some name>
```...where <somename> is a name of your choice no longer than 15 characters.  I match the NETBIOS name to my hostname but you don't have to.

Do I add that line under the [share] definitions or just outside of any category?

---

### Post by bab1 on 2013-11-18
> **jweaver682 said:**
> Do I add that line under the [share] definitions or just outside of any category?

Add the name in the [global] section.  Then you have to restart the Samba daemon so it re-reads the smb.conf file.  You do that with this command```
sudo service smbd restart
```

---

### Post by jweaver682 on 2013-11-18
> **bab1 said:**
> Add the name in the [global] section.  Then you have to restart the Samba daemon so it re-reads the smb.conf file.  You do that with this command```
sudo service smbd restart
```

I added the code and restarted the service but no icon appears from the network menu in windows. However, the server still works fine and i can access it via IP address, and I just added a shortcut to my desktop to the shared file.

---

### Post by TheFu on 2013-11-18
> **bab1 said:**
> This must be in the /etc/hosts file.  That's what the Samba server daemon named *nmbd* checks to convert to a NETBIOS name.  The nmbd daemon does not look for DNS served names per se, only /etc/hosts mapped names.  But like I said in the previous post you can bypass all of that by explicitly defining the NETBIOS name in the smb.conf file.

@bab1 - **THIS is brilliant!**  Thanks!    Though I pretty much always manage my /etc/hosts using a central machine and ansible to push any changes everywhere.

For DHCP static reservations, I let the DNS service in my dd-wrt router set the expected IP that is also in the /etc/hosts. We have less than 30 servers, so this isn't a big deal.

Why no internal DNS?   Well, when I was younger and the internet was too, I got hacked via DNS. The machine was 3 months behind on bind patches.

---

### Post by bab1 on 2013-11-18
> **jweaver682 said:**
> I added the code and restarted the service but no icon appears from the network menu in windows. However, the server still works fine and i can access it via IP address, and I just added a shortcut to my desktop to the shared file.

If your happy, then I'm happy.  If you want to fix it just let us know.

---

### Post by bab1 on 2013-11-18
> **TheFu said:**
> ...Though I pretty much always manage my /etc/hosts using a central machine and ansible to push any changes everywhere.

Every Linux machine the I know of first looks at its local /etc/hosts file.  Regardless of what you do to have a central hosts file, the local host always (by default) checks it own hosts file first.  Looking at the nsswitch.conf file reveals this```
hosts:          [COLOR="#FF0000"]files[/COLOR] mdns4_minimal [NOTFOUND=return] [COLOR="#0000FF"]**dns**[/COLOR] mdns4

```...the red says check the /etc/hosts file and the blue says check a DNS server.  The others are for avahi (.local).

I usually set my Samba servers NETBIOS name explicitly.  If I change the host name later on I don't get bit.  The hostname is NOT equal to the NETBIOS name this way.

---

### Post by jweaver682 on 2013-11-18
I think we are all good here. I really appreciate everyone's help.

---

### Post by TheFu on 2013-11-18
> **bab1 said:**
> Every Linux machine the I know of first looks at its local /etc/hosts file.  Regardless of what you do to have a central hosts file, the local host always (by default) checks it own hosts file first.  Looking at the nsswitch.conf file reveals this```
hosts:          [COLOR="#FF0000"]files[/COLOR] mdns4_minimal [NOTFOUND=return] [COLOR="#0000FF"]**dns**[/COLOR] mdns4

```...the red says check the /etc/hosts file and the blue says check a DNS server.  The others are for avahi (.local).

I usually set my Samba servers NETBIOS name explicitly.  If I change the host name later on I don't get bit.  The hostname is NOT equal to the NETBIOS name this way.
**Off-topic: **
Ansible is an enterprise configuration management tool in the vein of puppet, salt-stack, rex ...
By managing a templated hosts file centrally, I ensure that every server here gets the same hosts data for everything except their own hostname.  Ansible is setup to push changes to each server here individually for many configuration things.  /etc/hosts is just 1, but the setup handles nginx.conf, sshd_config, default crontabs for monitoring, satellite postfix configs, my personal settings, base package installations and purging nano ;) with Ansible.

With 5 or less machines, tools like ansible don't make much sense. As more and more machines are added, something like Ansible becomes more and more productive.

It is possible to use NIS+ to have a centrally managed hosts file, but as you point out, nsswitch.conf would need to be modified. NIS+ has been a core tool for UNIX installations for decades. Prior to NIS+, there was NIS (also called yp or yellow pages). There are still yp-commands on all our Linux systems.

What does all this mean?  To me is shows how much depth that UNIX/Linux systems have built-in. Whenever I need a solution for anything not related to gaming or video performance, chances are that it has been solved already and I just need to ask the correct question to discover an entirely new-to-me subsystem.

---

