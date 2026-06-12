---
title: "Package problems after update"
date: 2013-09-22
forum: General Help
---

### Post by Skilbride on 2013-09-22
Heya, Ubunto 12.4 just updated itself and now I cant use the software centre.  A red  warning sign appeared in the top bar and when I click on it it has the following error message:

E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.

I have looked for a package called "medibuntu.org_dists_precise_non-free_binary-amd64_Packages"  and tried to remove it but I cannot even find this package.

I'm very new at Ubuntu and am very stuck with this.  Any help would be greatly appreciated.  Thank you.

Sean Kilbride

---

### Post by ajgreeny on 2013-09-22
You say your 12.04 just updated itself, but what do you mean by that?  Are you still running 12.04 or have you moved to 12.10?

If you're not sure, let's see the output of ```
lsb_release -dc
``` in terminal, which will tell us.

However, you can probably overcome that error message problem simply by running the command ```
sudo rm /var/lib/apt/lists/*
```followed by ```
sudo apt-get update
``` and finally ```
sudo apt-get upgrade
```

---

### Post by Skilbride on 2013-09-22
Heya thanks for the response.  I am running 12.04.

I tried the "sudo rm /var/lib/apt/lists/*" command as you suggested, but I just get the message "rm: cannot remove `/var/lib/apt/lists/partial': Is a directory".  Do I need to delete the entire directory?

Thanks, 

Sean Kilbride

---

### Post by ajgreeny on 2013-09-22
OK, so let's see the output of ```
ls /var/lib/apt/lists/partial
```to see what's in there first, but all you will probably need to do is empty that partial folder as well, so use command ```
rm -R /var/lib/apt/lists/*
```Copy that very carefully as the **rm -R** command is all-powerful and could totally mess up your OS if you got it slightly wrong; particularly make sure you do not add any spaces after the rm -R that are not in my quoted command.

If that last comment of mine is too frightening to you, use two separate commands instead of the one recursive one
```
sudo rm /var/lib/apt/lists/partial/*
```
followed by ```
sudo rm /var/lib/apt/lists/*
```
Before you run the second command you may need to remove the partial folder with ```
sudo rmdir /var/lib/apt/lists/partial
```
Finally run the update/upgrade commands I gave you previously.

---

