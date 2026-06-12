---
title: "[SOLVED] Anyone know about MySQL?"
date: 2007-11-29
forum: General Help
---

### Post by tentwelveeight on 2007-11-29
I know this isn't exactly ubuntu related, but eventually it could be as my school is in the process of migrating from windows to Edubuntu.

Basically I am going to set up a mysql database that accepts parent applications to the school I work for via a php based website. The rub is that the school office needs a hard copy of each application, and would like the applications received via the web to match (as far as appearances) those received as hard copies. Make sense so far?

So I am wondering how I might go about exporting data from the MySQL database to a pre-formatted text document (or webpage) that I can then print out for the office staff. In the end nobody should be able to tell the difference between a completed application that has been printed out by the office at school using the MySQL content, and one that has been completed and printed out by a parent at home using MS Word or something.

I know this is possible because airline websites do it all the time when I buy tickets. I put in all my personal information on one webpage (and I assume it is entered into a database of some kind) and it spits out a boarding pass that is perfectly formatted for printing with all the info I entered. This is what I want to do. Can anyone help me out? Point me to a tutorial or at least tell me where to start looking? I'm using GoDaddy for the database and myphpadmin stuff. Thanks so much -joe

---

### Post by mardawi on 2007-11-29
what exactly are you having troubles with? Accessing the MySQL database or working out the PHP part to print reports that matches the hard copy? The thing that you are trying to do sounds trivial unless there is something that i didn't understand.

---

### Post by teryowen on 2007-11-29
sounds to me like you just need to write up a script in perl or whatever you intend on using, which will fetch the stored values from the Database, and then format the data write to a file, and done.

Personally i use perl, and thats what i would do make a script that when you enter the applicants names goes to the database gets all the values strcutures it to your format and saves to a file.

---

### Post by tentwelveeight on 2007-11-29
I can access the MySQL database fine and I can export the information from the database to a spreadsheet. What I need to do is export the information to a pre-formatted document instead of a spreadsheet, so I guess I need to know how to do the php part to print reports that match the hard copy. I certainly hope it is trivial, I'm just not experienced with this type of programming.

What I know how to do is get information from a php webpage to a MySQL database. What I need to do is go the other way. Take information from a MySQL database and put it into a php webpage. How do I do that? Thanks for the quick reply -joe

---

### Post by tentwelveeight on 2007-11-29
ok teryowen, thanks for the reply. I think that will solve my problem. Do you have any suggestions for where I might learn how to write such a script? I was hoping there might be another way that wouldn't require me to learn another lauguage, but if that is what is required, so be it. -joe

---

### Post by teryowen on 2007-11-29
Yes look at TT2, its a templating toolkit, which will help you greatly, so bascilly you will create a word document with no values and where you want values you will put funky things like:

[% FIRST.NAME %]

and then once the perl script gets the data it will send it through the template making you the file with all the information. so [% First.name %] would be replaced with Billy, something along those lines.

So over all you will have 2 seperate parts a) template b) the code to retrive data and send through template.

Here check this out:

[http://elmiko.x10hosting.com/scgi-bin/lotterytemplate.html](http://elmiko.x10hosting.com/scgi-bin/lotterytemplate.html)

thats the template which the data will be going into

now try this whole program out.
[http://elmiko.x10hosting.com/lotteryform.html](http://elmiko.x10hosting.com/lotteryform.html)

---

### Post by teryowen on 2007-11-29
Oh and as for not learning another program i remember being at a place where they used access and they made a template and then you could see all the data from the database displayed on the premade template, so yes you could go around learning this.

actually if you dont know perl, it might take quite the effort

so search google

---

### Post by KCPokes on 2007-11-29
Personally, if it is an issue with the hardcopy matching what is stored in the database, I'd consider generating PDFs on the fly, providing the office a copy and storing a copy in the database, along with information that will allow you to easily query the database for future reference.  Ensures that your copy matches theirs, plus if you stored the info in the table separate, you could update the info at a later time, thus generating the PDF again, if needed.  

Here's a quick example of class that'll allow you to create PDFs on the fly.  Of course you would first choose your language of choice, then find the solution.
[http://sourceforge.net/projects/pdf-php](http://sourceforge.net/projects/pdf-php)

Just a thought.

---

### Post by ecsd on 2007-11-29
You can export data from MySQL using a single SQL command, info a CSV (comma-separated values) or tab-delimited file, suitable to be read visually, or imported into a spreadsheet.
(SELECT, using the (look it up) "INTO OUTFILE filename" syntax.)

I would suggest getting used to doing simple command-line data manipulation in MySQL to get used to SQL syntax, then you'll see that getting the data out is very straightforward. 15 minutes' worth of creating and modifying tables, inserting data, updating single or multiple records, loading data into and out of mysql, and watching all the syntax errors until you get used to it, is all you'd need.

I suggest the WROX publishers book on MySQL, and of course the ultimate reference is always online at mysql.org.

---

### Post by tentwelveeight on 2007-11-29
Well it looks like I have a few different options and I'm not sure which one would be the best for the school. I'm going to mark this thread "solved" until I've had a chance to look over teryowen's example pages and make a decision, but if I need further help I may call on y'all again. Thanks for all the advice everyone. Cheers -joe

---

