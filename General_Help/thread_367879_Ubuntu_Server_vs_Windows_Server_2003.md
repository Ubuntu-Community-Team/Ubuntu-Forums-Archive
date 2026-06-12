---
title: "Ubuntu Server vs Windows Server 2003"
date: 2007-02-22
forum: General Help
---

### Post by Sjoram on 2007-02-22
I'm currently running a network with all Windows XP clients and a Windows Server 2003 domain controller/server.  I'm just wondering how easy, if possible, it would be to migrate to a network with a Ubuntu server with Windows clients.

I did explore Ubuntu desktop version a few months ago but needed the machine for other things so not currently using it.

I have a couple of questions, namely:

- Does having Ubuntu server require me to revert back to a workgroup structure within Windows? I assume there would be no method of authentication to user accounts on Ubuntu server from a Windows machine?
- My current domain controller/server runs as a web server, mail server, DNS server, DHCP server and proxy server.  I know that Ubuntu can run as a web server, DNS server and proxy server, but what about mail and DHCP?
- I had severe difficulties trying to integrate file-sharing facilities between the Ubuntu machine I had and my Windows machines a few months ago - Is it generally a difficult task or is it just me that found it hard?!

Any help on this would be greatly appreciated. Please bear in mind I've been all my life a Windows user and only recently started to actually start experimenting with Linux, and I was only on Linux for around 2-3 months before switching back to a Windows box, so I haven't had that much experience so far.  I do pick things up well as I go along, but please excuse me if I ask a lot of questions in reponse to any replies!!

Thanks a lot,
Sjoram :)

---

### Post by netkid91 on 2007-02-22
Ubuntu can handle acting as a mail and DHCP server, quite well in fact.  Samba *Can* act as a Win2K domain controller, but it is not recommended.  It would be much easier if you could migrate your client PC's to Ubuntu, as they can then use NIS for authentication....I suppose with some effort you could use an LDAP server along side SAMBA to provide a better authentication setup, but it would still be tricky.  In all honesty, everything but that should be easy.  As for your file sharing problem, Samba is a beast in that area too, and how you set it up all depends on what you want to do.  I'd recommend looking on SAMBA's website for documentation on that stuff.

---

### Post by Sjoram on 2007-02-22
Thanks for the reply. I do need to leave other machines on Windows, as some of the people that use them would have a fit if I migrated them to Linux (even though it is easier to use and less buggy!).

I had big problems trying to configure samba last time I seem to remember.

I'll get one of my spare machines set up with this and see how I go.

I note the server version of Ubuntu doesn't have a graphical interface?  I've spent my fair share of time in cmd in Win but the thought of no GUI at all scares me, to be honest! I assume I will need the server version though, for things like mail server, dns server etc.

I do like your sig!

---

### Post by netkid91 on 2007-02-22
The server and desktop version only differ in one or two ways, as you said, the server version has no GUI (which can be installed with apt), and comes with the server packages included (you don't have to install them over apt like the desktop CD), along with the fact that it has a text-based installer.  To get GNOME on the server install use:
sudo apt-get install ubuntu-desktop
However, on the note of GUI config tools, I have seen very few, but manuals can be your friend, and using the CLI to modify the text based config files can usualy give more flexibility than a GUI can, at the cost of usability.  I, myself, have always figured that Ubuntu could use some nice server GUI config tools, and being a member of the Desktop team, I'll make sure to put a few words in for the next release.
Anyways, need anything else, just ask (and if you want, PM me anytime).

---

### Post by gradedcheese on 2007-02-22
> 
Samba Can act as a Win2K domain controller, but it is not recommended. 


I've seen this setup at a place I worked and it worked perfectly fine.  I didn't see a problem with it.  Personally, I have it act as a 'workgroup server' but I could set it up as a domain controller if needed and I'm pretty sure it would be ok.

---

### Post by netkid91 on 2007-02-22
> **gradedcheese said:**
> I've seen this setup at a place I worked and it worked perfectly fine.  I didn't see a problem with it.  Personally, I have it act as a 'workgroup server' but I could set it up as a domain controller if needed and I'm pretty sure it would be ok.
SAMBA has full support for NT4 style domains, however Active Directory (AKA win 2K) support is still experimental, and should not be used in a production enviornment.
Edit: [PGINA ]("http://www.pgina.org/")could be helpful to you, it replaces the standard authentication system of Windows with a much more flexible one, which should mean you can truly set up Ubuntu as your authentication, etc. server without the mess of SAMBA, especially if you install a Windows NFS client on the machines.  It'd take a lot of setup, but it would be worth it in the end.[]("http://www.pgina.org")

---

