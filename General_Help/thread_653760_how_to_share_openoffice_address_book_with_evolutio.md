---
title: "how to share openoffice address book with evolution"
date: 2007-12-30
forum: General Help
---

### Post by Alco on 2007-12-30
Hello,

I am looking for a way to have Evolution and OpenOffice share the same address book database. Openoffice would be used primarily for editing the database and mail merge. Then I would like Evolution to be able to email contacts added in OpenOffice. 

I have thought along the lines of running an ldap service locally which would make the address book available to Openoffice and Evolution. I followed instructions on installing openLdap from help.ubuntu.com and was able to use ldapsearch to access the directory as  per the instructions. 

Now I have to figure out the clients configuration. Since i'm new to both ldap en ubuntu i have no idea how to do that. For example, after having setup the server following the instructions above, what do I enter in the 'address book properties' for 'server information' and port. Then, how do I configure access to the server from openoffice database? 

Or perhaps alternatives exist to share a database between the two clients. I have tried the 'Evolution local' connection from within OpenOffice, but this appears to give me read only access to the database. This in turn will make it difficult to import my existing address books into openoffice.

Thanks,
Alco

---

### Post by jovial on 2008-01-04
Hello

I've the same problem to share columns datas from EvolutionLocal contact in OOo 2.2 /2.3
Same probleme with sql instruction ORDER BY don't work.
The solution is to trait résult of SQL with oobasic.
I'm building an odt where I can insert an indidual address in 3/4 clic showind the contact (file as) ordered in a list box.
For merge try to drag and drop all your contact in calc after you can apply sort and filter
It seem to me it is possible to use a calc sheet as source for merge.

Bye

Jean-Luc

---

