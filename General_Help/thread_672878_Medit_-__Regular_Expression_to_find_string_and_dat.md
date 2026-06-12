---
title: "Medit -  Regular Expression to find string and date"
date: 2008-01-20
forum: General Help
---

### Post by steve_waters on 2008-01-20
Hey guys,

Been giving this a crack and thought there must be some clever girl/guy who can tell me the answer and save my hair falling out.

:)  History:
I have started using Grisbi money manager, and it is all good actually it is very nice and simple couple of quirks but other than that I really like it, however when I do a visa purchase my bank starts the transaction record with **"VISA PURCH dd/mm/yyyy** Some shop some where". So it screws up the nice Grisbi grouping of payees after it is imported. 

I have opened up the Grisbi storage file and it is an xml text doc and I have found where the transactions are kept, so all I want to do is do a search and replace within that document. There are 500 odd transactions so editing within Grisbi will be a nightmare they need to be batched.

:confused: Requirement: 

I want to replace (read delete) all instances of:

"**VISA PURCH dd/mm/yyyy**" within the file and be left with "**Some shop some where**"

I am using Medit which has regular expression search ability, but I am struggling with the syntax, even when I was programming it was the one thing that I never quite got.

Thanks for the help.......wow that was long winded to ask for a regular expression and it goes on..........

---

### Post by dagnabit dang doohickey on 2008-01-20
This command should produce a *newfile* with your desired result.
```
sed 's#^VISA PURCH[[:space:]]*[[:digit:]/]\{10\}[[:space:]]*\(.*\)#\1#' < *oldfile* > *newfile*
```

---

### Post by steve_waters on 2008-01-20
doohickey

Thanks for that!!! At work at the moment but will give it a try tonight, or maybe sneak into a virtual machine and have a try before I get home. 

That is nice I can put it in a bash script and feed my file in there each time I update it. 

Will let you know how it goes.

just on a side note, the regular expresion used there, is that common syntax or "sed" specific? Would the same expression work in Python for example?

Steve

---

### Post by dagnabit dang doohickey on 2008-01-20
I can't speak specifically about python usage, but the patterns between the pound signs are pretty standard regex stuff.

---

### Post by steve_waters on 2008-01-21
Nope she no work........ not sure if this makes a difference but the entire line I am looking for looks like this:

**<Tiers No="3" Nom="VISA PURCH 16/01/08 STEWY DAVIS AUTOMOTI" Informations="" Liaison="0"/>**

Where:
- "3" will change to represent the transaction number
- date will change
- name of shop will change


Thanks,
Steve

---

### Post by dagnabit dang doohickey on 2008-01-21
```
sed 's#^\(.*\)VISA PURCH[[:space:]]*[[:digit:]/]\{8,10\}[[:space:]]*\(.*\)#\1\2#' < *oldfile* > *newfile*
```
The command above will change:

**<Tiers No="3" Nom="VISA PURCH 16/01/08 STEWY DAVIS AUTOMOTI" Informations="" Liaison="0"/>**

into:

**<Tiers No="3" Nom="STEWY DAVIS AUTOMOTI" Informations="" Liaison="0"/>**


Some notes about the command:
1. If your date *always* appears as dd/mm/yy you can change \{8,10\} to \{8\}
2. If there is *always* just one space on each end of the date, you can remove the asterisk following each [[:space:]] and, if a shorter command is desired, you can also replace [[:space:]] with an actual space.

Trimmed version of the above command:
```
sed 's#^\(.*\)VISA PURCH [[:digit:]/]\{8\} \(.*\)#\1\2#' < *oldfile* > *newfile*
```

---

### Post by steve_waters on 2008-01-22
doohickey

you are a super star!!!!!

thanks for that worked like a charm, 500 transactions/lines processed in about half a second.

Thanks again,
Steve

(sed regular expression text and date solved)

---

