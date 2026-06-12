---
title: "guest session and virtualbox"
date: 2014-06-03
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-06-03
So i managed to get a virtualbox setup under the guest session using /var/guest-data and /etc/guest-session/skel
but i can't get the option of a bridged nic for the virtualbox in the guest session
does anyone know a way to enable bridged networks for virtualbox in the guest session, i know it is a permission issue

---

### Post by gordintoronto on 2014-06-05
What's your host, what's your guest? What makes bridged nics so essential in a virtual environment?

The nic in VB isn't even real, it's part of the fantasy.

---

### Post by pqwoerituytrueiwoq on 2014-06-05
Host is Ubuntu 14.04 64bit; Guest is Windows 7 32bit;
I have the virtualbox setup for the guest session user, i wanted to make the Guest OS connect to the windows domain controller
i want to bridge it to eth0, but the bridged option does not have anything in the NIC list

---

