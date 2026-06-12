---
title: "getent not working from bash script"
date: 2013-04-16
forum: General Help
---

### Post by steve-ss on 2013-04-16
Hi everyone
I have a script to create a new user in a Samba4 domain. The rfc2307 attributes are added in this script and are then available via e.g. getent passwd steve2 when the script has terminated. We are using sssd to get the info from the Samba LDAP.

Problem: Inside the script, getent user steve2 returns nothing, so we cannot e.g. create a home directory for the user:
mkdir /home/users/steve2
chown steve2 /home/users/steve2
because user steve2 is unknown to the shell. We can only use the numerical uidNumber for steve 2 to set the correct permission. Under openSUSE the exact same script works fine: getent passwd steve2 works fine and the username steve2 is available inside the script. With 12.10, the username steve2 is only available AFTER the script has terminated.

Question: how do I get getent passwd to work inside the script and no only after it has terminated?

Cheers,
Steve

---

### Post by steve-ss on 2013-04-17
> **steve-ss said:**
> Hi everyone
I have a script to create a new user in a Samba4 domain. The rfc2307 attributes are added in this script and are then available via e.g. getent passwd steve2 when the script has terminated. We are using sssd to get the info from the Samba LDAP.

Problem: Inside the script, getent user steve2 returns nothing, so we cannot e.g. create a home directory for the user:
mkdir /home/users/steve2
chown steve2 /home/users/steve2
because user steve2 is unknown to the shell. We can only use the numerical uidNumber for steve 2 to set the correct permission. Under openSUSE the exact same script works fine: getent passwd steve2 works fine and the username steve2 is available inside the script. With 12.10, the username steve2 is only available AFTER the script has terminated.

Question: how do I get getent passwd to work inside the script and no only after it has terminated?

Cheers,
Steve

On further investigation it takes 10 seconds for the new user to emerge from LDAP. Maybe something to do with the sssd disk cache. Anyay, we solved it by adding a 
sleep 10
after adding the user but before doing anything else with him:)

---

