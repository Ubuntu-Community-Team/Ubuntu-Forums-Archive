---
title: "Pseudo-MDM Style Enterprise Solution"
date: 2020-07-16
forum: General Help
---

### Post by epit-av on 2020-07-16
Hello everyone,

I'm working to transition my school district towards Ubuntu, but I'm wondering what my best options are for a number of different management problems.  I'm not necessarily looking for someone to solve them all for me, but rather point me in the right direction.  I'm no stranger to Linux, but I am definitely not familiar with managing Linux in the enterprise.  If you could give me some pointers for the following subjects, I'd really appreciate it.
[B]
Software Management


[/B]This is where I'm lost.  I really don't know the best way to go about this.  Obviously I can SSH into the devices and apt-get whatever is requested, but that's not optimal.  Devices might be offline, taken home, etc. and I'd have no way of knowing.  Should I create a repository, add it to the sources, and put all my software in it?  I've already had web calls with Chef, Puppet, etc. and their pricing is just something I can't afford.  For a simple scenario, let's say a teacher wants GIMP installed on 28 student laptops.  What's the best way of going about this and getting it done?

[B]
Remote Access

[/B]This is taken care of for the most part, we have an OS agnostic solution in place.
[B]

User Management

[/B]I have this one down pretty good.  I'm using SSSD as my LDAP connector to G Suite.  Staff/Students can use their G Suite accounts to log in.  They can do things like cat files in /etc/ which I'd prefer to get rid of.  If I get my G Suite groups working in SSSD that won't be much of an issue, though.  I understand permissions enough to limit certain groups once I get that completed. 

If anyone else has any other general tips for the enterprise, like any FOSS management tools, PLEASE let me know.  I really appreciate everything.  I'm doing a lot of research, but a lot of things I find aren't necessarily relevant/affordable.

---

### Post by kneutron on 2020-07-16
> [COLOR=#000000]For a simple scenario, let's say a teacher wants GIMP installed on 28 student laptops. What's the best way of going about this and getting it done?

--Ansible is free, but you should really run your YAML through a linter first. Having a job fail 63 times can get dam' frustrating.

REF: 
[/COLOR][https://www.linuxtoday.com/developer/automate-your-infrastructure-with-ansible.html](https://www.linuxtoday.com/developer/automate-your-infrastructure-with-ansible.html)

[https://www.linuxtoday.com/it_management/manage-your-workstation-with-ansible-automating-configuration-180326080514.html](https://www.linuxtoday.com/it_management/manage-your-workstation-with-ansible-automating-configuration-180326080514.html)

[https://code.tutsplus.com/tutorials/automate-all-the-things-with-ansible-part-one--cms-25931](https://code.tutsplus.com/tutorials/automate-all-the-things-with-ansible-part-one--cms-25931)[COLOR=#000000]
[/COLOR]

---

