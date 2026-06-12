---
title: "How to import cvs contacts in Evolution"
date: 2007-05-05
forum: General Help
---

### Post by ziofil on 2007-05-05
Hi there!):P 
I managed to import a csv contact list in evolution. 
Since it's been a bit tricky and since here in the forum I found no solutions, I'll explain how I did it.

1- copy in an openoffice spreadsheet your contacts from hotmail, yahoo, whatever. (just select the list, copy and paste special in openoffice) Do not choose the comma as separator: we need name and surname to be in the same column.

2- add a row on the top and write SURNAMES and EMAILS (or other labels if you have other columns) on the corresponding columns. SURNAMES must be on the top of column with both name and surname.

3- install mozila-thunderbird
```
sudo apt-get install mozilla-thunderbird
```

4- save your openoffice file as a .csv file selecting the ";" as separator.

5- open with gedit the file you just created and with ctrl-H replace with nothing the commas that eventually separate the name from the surname.

6-again replace the ; with commas and save the file. (in this way every field is between "" and is separated from the other fields with a comma, and no other commas are involved!)

7- import in thunderbird the csv file you just created. Be careful when you select which column to be the emails and the names:  SELECT "SURNAME" TO BE THE COLUMN YOU PREVIOUSLY NAMED "SURNAMES". Do not import anything else (unless you have extra columns). do not import NAME (you already have both in SURNAME)

8- export the ldif file of your contacts from thunderbird.

9- import in Evolution the ldif file (File >> import >> single file, etc...). Now the contacts have name and surname under Full name and the email in the correct place!

10- uninstall thunderbird if you don't need it
```
sudo apt-get remove mozilla-thunderbird
```

it worked for me (after an hour of yelling!), I hope it will work also for you!
bye

:guitar:

---

### Post by ziofil on 2007-05-05
sorry, the title should have been  "How to import [COLOR="Red"]csv[/COLOR] contacts in Evolution"

---

### Post by cdillard-hsp on 2007-10-10
What a real freaking pain in the butt it is to import a CSV file into Evo contacts!  This sucks.  Would it be too hard to have a field mapping step in the stupid Import wizard???

I love Linux but I have to say that Evolution is the biggest pain in the butt with some things.  Problem is, I'm stuck with it since T-bird doesn't have any PIM features, which I need for work.

Argh!

---

### Post by nwstephens on 2008-06-03
What a pain!  This worked, but only after I used DISPLAY NAME instead of SURNAME from withing Thunderbird.

---

### Post by onyxbits on 2008-07-05
> **cdillard-hsp said:**
> What a real freaking pain in the butt it is to import a CSV file into Evo contacts!  This sucks.  Would it be too hard to have a field mapping step in the stupid Import wizard???


Well, if you insist on doing it the hardest way possible, you shouldn't be to surprised, if it becomes a pain in the butt ;). Using [CSV2LDIF]("http://www.onyxbits.de/node/13") or [csvconv]("http://www.onyxbits.de/node/11") would have been a lot less trouble. 

I think, I should add a template for this kind of thing, seems like a not to uncommon problem.

Edit: NVM, did not realize, that this was a rather old thread.

---

