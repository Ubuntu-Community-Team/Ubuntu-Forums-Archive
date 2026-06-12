---
title: "Programs and user-information"
date: 2006-10-30
forum: General Help
---

### Post by rpw on 2006-10-30
Hello,

I'm not sure at all, if this is the right forum to post (to the admins: if it's the wrong forum, just move the posting), and the meening of this posting might be a little bit difficult to explain at all. Also this is not related only to K/X/Ubuntu, not even to any Linux-distro .

It might be related to the desktops AND the programs that need configuration information. Let me also say I'm not a programmer at all, so I'm not sure, wheather this suggestion is possible or not.

OK, here we go... ;) 

Wouldn't it be a good idea to have one place to store informations, that are needed for a lot of programs to work at all - like mailclients?

Today you install a system, create a user, and then you configure every program that needs configuration informations (username, password, thhp-address, ...).

When you choose to switch one of these programs (for example the mailclient) you have to setup the new mailclient and give it all the informations you've typed in before.

And maybe it would be even worth thinking about things like contacts, links, and some others.

What about a little database, for example SQLite, that stores all the needed informations, and the programs just using this informations?

Here are some informations, I can think of:
- Userinformation (all informations, name, address, etc. that could be used in OpenOffice writer to create new user templates
- Mail (hoster, username, password)
- VOIP (hoster, username, password)
- Messenger (hoster, username, password)
- Contacs (persons with their complete address, mail, phone, ...)
- Favorites (to me favorites in a browser are just different contacts)

There would be some more advantages, for example if user installs a new system on another computer. Just create a backup of this database (a database dump for example), import it in the new system, and you are ready to go and use the applications on this new installed system.

Maybe there a lot more opportunities, I haven't thought about.

As I sayed before, this is not related only to Ubuntu, even not only to a special desktop. The developers of the different desktops and the developers of the programs would have to communicate and create a solution that fits their needs.

Regards,

rpw

---

