---
title: "Upgraded to 12.10 And Can't Create A Second User Account"
date: 2013-05-09
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-05-09
Hello,

I just upgraded from 12.04 to 12.10 and I can't create a second user account.  System Settings > User Accounts does not ask for a password when creating an account, so a user gets added; but the account is disabled.

Any help appreciated.

Hannibal

---

### Post by gnusci on 2013-05-09
Your system may need the following commands:

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

Otherwise something else may be very wrong!

---

### Post by coljohnhannibalsmith on 2013-05-10
Hello,

I finally figured out how to create a second user accout.  I had to click on the empty space where the password would go; it the showed itself as a button and opened up.  that action enabled the user account.

Thanks Hannibal

---

