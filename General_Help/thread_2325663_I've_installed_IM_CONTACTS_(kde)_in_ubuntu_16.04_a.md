---
title: "I've installed IM CONTACTS (kde) in ubuntu 16.04 and  can't remove"
date: 2016-05-24
forum: General Help
---

### Post by hhh81 on 2016-05-24
**[SIZE=5][SIZE=6][COLOR="#FF0000"]EDIT: I HAVE SOLVED EVERYTHING SOMEHOW ,DELETE THIS POST/THREAD PLEASE. [/COLOR][/SIZE][/SIZE]**



HI
I've installed IM CONTACTS (kde) in ubuntu 16.4 and can't remove now, from ubuntu software
if i click to remove in 'ubuntu software'  doesn't work, "remove" and "launch" options buttons will back every tyme.
I have a road sign (wrong way) in up right corner bar of ubuntu, if i right click in it says:  
"An error occurred, please run package manager from the right click menu' or apt-get in terminal to see what is wrong, the error message was : error brokencount > 0 .
this usually means that your installed packages have unmet dependecies.."

I think that i must remove  "im contacts" and "kde im log viewer" . how can i do? i tried some commands in terminal, like sudo apt-get remove something...  but doesn't work... help me please.

edit: now i can't remove EMPATHY  neither ,it seems to use some kde dependecies.

enrico@enrico-System-Product-Name:~$ sudo apt-get remove --auto-remove empathy
[sudo] password for enrico: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 account-plugin-aim : Depends: empathy (= 3.12.11-0ubuntu3) but it is not going to be installed
 account-plugin-jabber : Depends: empathy (= 3.12.11-0ubuntu3) but it is not going to be installed
 account-plugin-salut : Depends: empathy (= 3.12.11-0ubuntu3) but it is not going to be installed
 account-plugin-yahoo : Depends: empathy (= 3.12.11-0ubuntu3) but it is not going to be installed
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
 mcp-account-manager-uoa : Depends: empathy (= 3.12.11-0ubuntu3) but it is not going to be installed
                           Recommends: ubuntu-control-center-signon but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


EDIT:  I HAVE SOLVED EVERYTHING  SOMEHOW  ,DELETE THIS POST/THREAD PLEASE.

---

