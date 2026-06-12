---
title: "Desperate - Restoring Evolution contacts"
date: 2013-02-22
forum: General Help
---

### Post by Northpoint on 2013-02-22
Hello.

Im in deep do-do as I have a customer that was running Ubuntu 10.04 32bit with evolution email client. They had issues with the install and I had to re-install over the old installation. I did a backup of evolution but the contacts are all missing. After further investigation into this I discover that the client was putting the contacts  NOT in personal but in Ubuntu One folder. Therefore, I was thinking they would probably be backed up on the cloud (?). However, I tried to log into ubuntu one with the clients email and password and they have no record of the email address. This is the only email address they have setup in evolution. Therefore I believe that they were just storing their contacts there for lack of a better place. They never registered with ubuntu one.

Thought the restore would recover those contacts. They did recover 2 email "groups" in the personal folder. 

I think that its weird that evolution would not also backup those contacts placed in the Ubuntu one folder (???). Perhaps they felt if they did it would be redundant?

Therefore, Am I out of luck or is there anything else to try? Has anyone ran into this before????

Thanks,

Northpoint

---

### Post by Northpoint on 2013-02-23
After hours of working on the situation I finally resolved it. But I would like to share some info that may help others in the future.

Ubuntu includes "Ubuntu One" cloud storage which appears to be a plugin/addon to the evolution email client. If you do not have a U1 account then using the address book called "Ubuntu One" in evolution means you could lose all your saved addresses. 

Normally, If reinstalling or doing whatever with your ubuntu install you would run the integrated backup program in evolution. However, evolution will not backup the U1 address book. I also noticed that when installing evolution and then saving an address the default address book seems to be U1. This can cause alot of problems for those not tech savy. 

Therefore, restoring evolution will leave you with a blank address book. Isnt that nice? 

How I recovered it? Well, I did check U1 to see if my client had an account - they didnt. So, I logged into their email provider via browser and found a address book there. I downloaded it as a vcard and then went thru their deleted emails (which evolution did backup) and scrubbed more email address and added them to it. Then I backed up the finished address book to a vcard to import to thunderbird as I will not use evolution anymore and neither will any of my clients if I can help it.

I dont care for evolution anymore.

1. Version changes prevent you from restoring backups.
2. No forum except a email support option.
3. Will wipe your stored email password if for some reason you cannot connect to your email server.
4. Can be a hassle to setup depending on your email provider.

CUL8R

Northpoint

---

