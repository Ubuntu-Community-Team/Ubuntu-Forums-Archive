---
title: "msktutils create in AD child OU"
date: 2020-07-29
forum: General Help
---

### Post by klaxmaster on 2020-07-29
EDIT: SOLVED:

You apparently have to START with the most deep layer, and work your way out. Which has got to be the most conter-intuitive thing I have encountered in a long time.

IE: [HTML]'OU=DEVICES,OU=KALX'[/HTML]  instead of [HTML]'OU=KLAX,OU=DEVICES'[/HTML]

This isn't mentioned in any of the MAN pages I looked up, nor did I find anything hinting at this in any of my search terms which included nested, child, OU, AD, LDAP,  etc.

Discovered it on my own, And I do not know why I decided to try it. I do not have experience with AD or LDAP. I'm just a windows user level, and ubuntu support level, starting my Sys Admin path.


[B]Original Post Below
[/B]__________________________________

I'm a bit stumped. Cant seem to find the solution to adding a computer to the correct OU, which is nested in another OU on my Windows AD server.  I can not change the AD structure (as it is not my choice, and i have to work with it)

More Details:
AD Structure:
[HTML]AD01.klaxmaster.local > Klax(OU)>Devices(OU)[/HTML]
(The default computer location would just be AD01.klaxmaster.local>Computers)

Command being used:
[HTML]msktutil -N -c -b 'OU=KLAX,OU=DEVICES' -s ADTEST/adtest.klaxmaster.local -k my-keytab.keytab –-computer-name ADTEST –-upn ADTEST$ –-server ad01.klaxmaster.local –-user-creds-only[/HTML]

I believe I have tried every combo of CN= and OU=.  But i can't get it into the child OU 'DEVICES'

I CAN get it to add the object to OU=KLAX making it at the same level as the child OU=DEVICES, but i need it inside, not parallel.

I can not settle for having it placed it in the default computers list, As I need to replicate what my office uses, which i have no control or say in changing.

 The actual error I get is:
[HTML]
Error: ldap_add_ext_s failed (No such object)
           additional info:0000208D: NameErr: DSID-03100288, prolem 2001 (NO_OBJECT), data 0, best match of:
           'DC=klaxmaster,DClocal'
[/HTML]


EDIT:
I am left wondering if I just can't figure out the SYNTAX or if msktutils just cant add an object in a nested OU (Child OU)
the latter seems unlikely, though, as i can authenticate with the admin user that is in the same depth but in
[HTML]AD01.klaxmaster.local > Klax(OU)>Employees(OU)>klax.master[/HTML]

---

