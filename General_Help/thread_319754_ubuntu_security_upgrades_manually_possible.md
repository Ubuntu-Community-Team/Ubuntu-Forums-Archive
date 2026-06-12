---
title: "ubuntu security upgrades manually possible??"
date: 2006-12-16
forum: General Help
---

### Post by ambar on 2006-12-16
hi all
I am quite new to Linux. Can anybody please help me with the following problem:

problem:
The upgrade manager shows that there are 48 upgrades available;they amount to 61.3mb total.
I don't have a very high bandwidth connection  and was just wondering if he manual download cud save me megabytes of download  .

 i wanted to know if there is some other method of downloading them and backing them up  so that i can reinstall the upgrade *offline* .


thank you
ambar

---

### Post by SpongeBob SquarePants on 2006-12-16
What you can do using "Adept" (system>Adept) is install the updates one at a time. You just need to bring up the list of potential updates and apply them individually.

---

### Post by ambar on 2006-12-16
thank u for the reply. but i think u understood me wrongly.

The files that are download as updates are installed right? If in future i format my system i will have to again download 61mb. i want that the files remain in my system as some sort of executable form(dump as one may call it) which can be later on installed in case of a reformat.

thank you again
ambar

---

### Post by az on 2006-12-16
> **ambar said:**
> thank u for the reply. but i think u understood me wrongly.

The files that are download as updates are installed right? If in future i format my system i will have to again download 61mb. i want that the files remain in my system as some sort of executable form(dump as one may call it) which can be later on installed in case of a reformat.

thank you again
ambar

All packages are downloaded to /var/cache/apt/archives

That directory does not get cleaned up unless you apecifically do it - so all packages you fetched in the past from the archives are still there.

You can back up that directory to preserve those packages.  However, if there is a newer version of those packages available when you later reinstall and dump them back there, the package manager will ignore the old version and go ahead and download the ones that have new versions.  You can make a home-made archive out of that directory but that gets complicated.

---

### Post by ambar on 2006-12-16
thank you so much .this clears my doubt.

---

