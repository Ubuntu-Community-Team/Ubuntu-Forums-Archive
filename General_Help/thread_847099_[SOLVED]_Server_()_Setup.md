---
title: "[SOLVED] Server (?) Setup"
date: 2008-07-02
forum: General Help
---

### Post by Stunts on 2008-07-02
Hello everyone.

I have a question for those among you who are true networking experts.

I am part of a research group in molecular biology. Since I'm the most computer savvy person in this group I was requested to setup a solution for the group.

We need some way to share files and trade messages over a local network. The files can be very large (up to 200Mb or even lager in some exceptional cases) and a forum like way to trade messages would be ideal.

Most (OK, so I'm the only linux user) of my colleges are windows users. They know how to do web browsing, and with a bit of effort I could get them to use a simple file sharing solution (like windows shared folders), but I don't think FTP could be acceptable for them... Most of them are not so willing to learn new computer "tricks" (You'd think different of scientists, wouldn't you?)

The file sharing should be only accessed by members of our group, and not public to everyone on the network.

We have several older PC's available that can be used as servers if necessary.

My skills with this sort stuff could be a limiting factor... Just to let you know which level I'm on:
 - I can program in Perl and Python;
 - I have successfully setup a PC for multiple remote logins in windows;
 - I have (much more easily I must say) done the same with a linux PC;
 - I have general notions of networking(IP DNS MAC adress and all those concepts);
 - I know a bit of HTML too;
 - I have compiled several programs from source (just to let you know I like tinkering with this);
 - I've only got 8 months of experience with linux and I absolutely love it.

I hope I was able to express my problem and the solution I need to find...
Anyone got some good advice on this? Thank you very much for all your replies.

For the mods - I'm sorry if I'm posting this in the wrong category!

---

### Post by dominiquec on 2008-07-02
I'd suggest that you look at some document management software.  An example would be Contineo ([http://contineo.wikispaces.com](http://contineo.wikispaces.com)).  There's also Alfresco ([http://www.alfresco.com/](http://www.alfresco.com/)) and Epiware ([http://www.epiware.com/](http://www.epiware.com/)).  Reason I suggest these over straightforward file sharing is you'll want some degree of access control, version control, tagging, and search capabilities, among others.

You might also want to look at IBM's knowledge management for life sciences ([http://www-304.ibm.com/jct03004c/businesscenter/smb/us/en/lifesciintro](http://www-304.ibm.com/jct03004c/businesscenter/smb/us/en/lifesciintro)).  Not necessarily for a product to buy but for ideas on what and how to implement.

(Oh, and disclaimer: I used to work for IBM, but it's been a while.)

---

### Post by hyper_ch on 2008-07-02
document sharing:  samba
messaging (if forum): apache, php5, mysql + phpbb3/smf forum software

---

### Post by Stunts on 2008-07-03
Hi guys!
Thanks for your replies!
Samba and phpbb3 was what I had in mind at first, but I was looking for something a bit more integrated.
I'll see what I can do with Epiware.
It seems to be just what I need!

Thanks again! It's great to be able to count on such a great community!

---

### Post by Dr Small on 2008-07-03
> **Stunts said:**
> Hi guys!
Samba and phpbb3 was what I had in mind at first, but I was looking for something a bit more integrated.


There is also MyBB, PunBB, FluxBB and IBB out there. There are alot of different choices.

---

