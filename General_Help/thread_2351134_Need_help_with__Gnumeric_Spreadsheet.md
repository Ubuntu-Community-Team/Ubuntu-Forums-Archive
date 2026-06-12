---
title: "Need help with  Gnumeric Spreadsheet"
date: 2017-01-31
forum: General Help
---

### Post by linuxyogi on 2017-01-31
Hi I am using Gnumeric Spreadsheet and I want Gnumeric to keep  subtracting from B1 whatever figure I add below it. 

Hi have added an example Spreadsheet. Please tell me how to add the formula.

See attachment.

---

### Post by Dennis N on 2017-01-31
I slightly modified to allow any starting value in b1:
See attachment, where:
cell b1 contains the resulting total
cell b2 contains the formula **=b1-sum(b3:b52)**

allows 50 debt values to be included.

---

### Post by TheFu on 2017-01-31
$B$1 will keep that cell in any formulas, just like with every other spreadsheet.

What do you mean by "add below it?"  What are you "adding?"
Typing something like "=B1-B2" ... then "=b2-b3" in the next cell below?

---

### Post by linuxyogi on 2017-01-31
In my example file file (see attachment) 1000 is my monthly budget and below that are my daily expenditures. What I want Gnumeric to do is subtract 100 then 200 (from1000) and so on.

---

### Post by Dennis N on 2017-01-31
> **linuxyogi said:**
> In my example file file (see attachment) 1000 is my monthly budget and below that are my daily expenditures. What I want Gnumeric to do is subtract 100 then 200 (from1000) and so on.

This is what post #2 does. Does it not?

---

### Post by linuxyogi on 2017-01-31
> **Dennis N said:**
> I slightly modified to allow any starting value in b1:
See attachment, where:
cell b1 contains the resulting total
cell b2 contains the formula **=b1-sum(b3:b52)**

allows 50 debt values to be included.

This is what post #2 does. Does it not?

Sorry but I dont know where to add > cell b1 contains the resulting total
cell b2 contains the formula **=b1-sum(b3:b52)**


Doing this for the first time.

---

### Post by Dennis N on 2017-01-31
enter your total budget in cell b1
enter the formula [FONT=Courier New]**[COLOR="#FF0000"]=b1-sum(b3:b52)[/COLOR]**[/FONT] in cell b2
then you just type in the debt values under that in cells b3,b4,b5, and so on. as each is typed in, the amount remaining will show in cell b2. Try it.

---

### Post by linuxyogi on 2017-01-31
@[**[COLOR=#000000]Dennis N[/COLOR]**]("https://ubuntuforums.org/member.php?u=321222"). It worked. Thanks a lot.

---

### Post by Dennis N on 2017-01-31
Glad to help. Spreadsheets are fun.

---

