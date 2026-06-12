---
title: "Is it Okay to Delete First Account Created"
date: 2014-08-10
forum: General Help
---

### Post by shai3 on 2014-08-10
Hi,

I have a new Linux box. It was pre-installed with Ubuntu 14.04 by System76 from whom I bought it.

I had serious problems with the first account I creating using the wizard that ran when I turned on the machine. (There was a big mess with the password keychain and I couldn't use an SSH key I had installed... blah, blah I'm not writing about that here.)

It seemed the easiest thing for me to do was start over by creating a new user account. Everything is going well with the new user account. I have successfully set "administrator" privileges for this new, second, account.

Is there any reason not to delete the original botched user I created with the wizard? Are there any hidden priviledges to that account that I don't know of (I'm new to Ubuntu)?

If it is okay to delete the account, is it considered better or more reliable to use the terminal as opposed to the Accounts UI in system settings?

I want to delete the user AND the home directory for that user. Assuming the account name is "joe" is the following correct?

```
userdel --remove joe
```

Thanks,

Shai

---

### Post by grahammechanical on 2014-08-10
If you are new to Ubuntu then use the GUI utility provided by the Ubuntu developers. With the terminal it is the user who has to be "better" and "reliable." Only a user who has Administrator privileges can create users and assign Administrator privileges. Likewise, with the removal of users and privileges. If you have been able to create a new administrator account then what can go wrong if as the new user you delete the old administrator account? The system is designed to work this way.

Regards.

---

### Post by nerdtron on 2014-08-10
I tried it once. I you are not sure on what you are doing, I'd say just reinstall and create the user you wanted. It's ok to add/delete other users you have created but I don't think it is worth it deleting the (first) default user account.

---

### Post by coldcritter64 on 2014-08-10
> **nerdtron said:**
> I tried it once. I you are not sure on what you are doing, **I'd say just reinstall and create the user you wanted**. It's ok to add/delete other users you have created but I don't think it is worth it deleting the (first) default user account.
You can add a second account and with the GUI tools set it as an admin then remove the first and so on; you must have the second account added to the sudoers file etc. for it to work, it is a lot of messing around to set up cleanly this way. The second account will end up as user 1001 etc.  Not worth the effort in my opinion OP.

That's why I really agree with the bolded section in the above quote box OP. Especially if you haven't done much in the system76 install customization or set up wise. Live dvd or live usb installation to a complete drive with no dual booting or anything is real quick and easy (and clean;)). Cheers, coldcritter64

---

