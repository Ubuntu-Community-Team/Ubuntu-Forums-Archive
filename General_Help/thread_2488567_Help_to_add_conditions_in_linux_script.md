---
title: "Help to add conditions in linux script"
date: 2023-07-09
forum: General Help
---

### Post by manroot on 2023-07-09
[FONT=Arial]Hello, I have a script where I monitor some notifications received via telegram, these notifications are redirected to a file called input.txt and the script is fed precisely by this file.[/FONT]
[FONT=Arial]Example of the content inserted in input.txt:

[/FONT]Example of the content inserted in input.txt:[FONT=Arial]
[/FONT]> #Price_Notification_ProductABC
Price: 0.006813
change: +1.6%
Count Number: 1


#Price_Notification_ProductABC
Price: 0.006969
change: +2.3%
Count Number: 2


#Price_Notification_ProductABC
Price: 0.007060
change: +1.3%
Count Number: 3


#Price_Notification_ProductABC
Price: 0.007300
change: +3.4%
Count Number: 4


#Price_Notification_ProductABC
Price: 0.007453
change: +2.1%
Count Number: 5

[FONT=Arial]Output after script execution:
[/FONT]> #Price_Notification_ProductABCPrice: 0.006813
change: +1.6%
Count Number: 1


#Price_Notification_ProductABC
Price: 0.006969
change: +3.9%
Count Number: 2


#Price_Notification_ProductABC
Price: 0.007060
change: +5.2%
Count Number: 3


#Price_Notification_ProductABC
Price: 0.007300
change: +8.6%
Count Number: 4


#Price_Notification_ProductABC
Price: 0.007453
change: +10.7%

Count Number: 5

[FONT=Arial]The function of the script is to add incrementally the item “change:”[/FONT]
[FONT=Arial]Up to this point everything is ok and the script has been working, however I have two problems and I need to implement two conditions for this to be solved.

[/FONT]
[FONT=Arial]1- The percentage needs to be calculated incrementally/increasingly, within a window of 0 to a maximum of 30 minutes between one notification and another, 
from minute 31, the incremental calculation of the percentage needs to be reset/restarted, starting a new one calculation cycle

[/FONT]
[FONT=Arial]2- I need a condition where the value contained in the item “Price:” in the current notification is not less than the value of the previous notification, example:
[/FONT]
[FONT=Arial]Current notification:
Price: 0.006825
[/FONT]
[FONT=Arial]Previous notification:
Price: 0.007453


[/FONT]
[FONT=Arial]If this occurs in any of the 2 scenarios, the cycle must be automatically restarted and the sum of percentages reset to zero.[/FONT]
[FONT=Arial]Any ideas how I can solve this little problem in my script?

[/FONT]
[FONT=Arial]I have the 2 scripts below and they both do the same thing, if you can help me tweak the 2 scripts I’d appreciate it
[/FONT]
[FONT=Arial]Script in perl:
I execute as follows:
perl -lp ./perl.pl input.txt

[/FONT]> #!/usr/bin/perl -lp

if (/^#Price_Notification_Product/) {
  $prod = $_;
} elsif (/^change: ([^%]*)%/) {
  $products{$prod} += $1;
  $_ = "change: +$products{$prod}%";

[FONT=Arial]Script with awk:[/FONT]
[FONT=Arial]./awh.sh

[/FONT]> #!/bin/bash

awk '
/^#Price_Notification_Product/ {
  prod = $0;
}
/^change: / {
  gsub(/[+%]/,"",$2);
  products[prod] += $2;
  $2 = "+" products[prod] "%"
}
1' /opt/scripts/input.txt
[FONT=Arial]
[/FONT]

---

### Post by TheFu on 2023-07-09
Please use forum _code tags_, not quotes and italics.

I've re-re-read the problem and you've lost me.  If you need to retain values for 30 minutes, then you'll want to store every change in value for a specific product that happens in that 30 minute period with a timestamp.

Think of it as two scripts.  1 that fills a DB with the values/timestamps and another that reads the DB looking for changes.  Depending on whether you can flush the DB daily, you would choose a different DB.  If you can flush it every 30 minutes, some other choices can be easily handled in perl using Tie:: modules.  I suspect you may want to have a rotating 30 minute period and just drop old values from the DB as they expire?  Can't tell from the description.

Anyway, once you have all the data stored and cleaned up as needed, then the calculations become easier, since you have all the data.

---

### Post by manroot on 2023-07-09
> **TheFu said:**
> Please use forum _code tags_, not quotes and italics.

I've re-re-read the problem and you've lost me.  If you need to retain values for 30 minutes, then you'll want to store every change in value for a specific product that happens in that 30 minute period with a timestamp.

Think of it as two scripts.  1 that fills a DB with the values/timestamps and another that reads the DB looking for changes.  Depending on whether you can flush the DB daily, you would choose a different DB.  If you can flush it every 30 minutes, some other choices can be easily handled in perl using Tie:: modules.  I suspect you may want to have a rotating 30 minute period and just drop old values from the DB as they expire?  Can't tell from the description.

Anyway, once you have all the data stored and cleaned up as needed, then the calculations become easier, since you have all the data.


Hello, thanks for the reply


I don't have any restrictions on making the kind of changes that are necessary, I just need a way to define what those changes would be, and I'm looking for help because I'm not a programmer and I understand the basics of scripts, but I believe that with good instructions I can manage move on
Could you help me assemble the necessary scripts?


About the database, I'm still in a testing environment but I can implement it if necessary, at the moment I'm using a txt file to feed my tests with information.
And yes, I can discard the data after 30 minutes without any problems


Thank you very much!

---

### Post by dragonfly41 on 2023-07-10
Since you are not a programmer I suggest using a simple GUI to automate the process.

There are quite a few but one favourite I use often is Actiona (although dated back to Actionscript2 days and the developer has moved on).

Install

sudo apt install actiona

The GUI shows a number of Qt widgets and if you have already  input.txt from preprocessing, read in that file then parse into variables.

If the input file is say *.csv or *.ini it is easier to parse into Actiona variables. But play around. You can embed Python or other help scripts in Actiona Resources in toolbar then run them in Command widget.

I would structure input as actionscript (like json). I use Sublime Text as editor (rather than Code editor) since the fonts are tiny (for my eyes) in Actiona. Then I paste into Actiona editor.

But there are many like GUI's around you can leverage for automation scripting

---

### Post by TheFu on 2023-07-10
> **manroot said:**
>  Could you help me assemble the necessary scripts?

Sorry, I don't teach beginning programming. Not my skill. Adding a DB, if that truly is needed, would bump the difficulty to intermediate skill level.  A DB doesn't HAVE to be a big DBMS. It can just be a maintained text file. Just be certain that only 1 process writes to the file at a time and that process opens the file for exclusive use.

I have lots and lots of questions to fill in the requirements more clearly. I think anyone coding this would need to know.  
Does this run 24/7 or every 5 minutes or every 30 minutes?  Vastly different answers would result.  
Are there 10 products being watched, hundreds, thousands, millions? Vastly different answers would result.  The program can keep all the price data, timestamps in memory for 100 products, but it really shouldn't for much more. Some sort of temporary storage is needed to ensure no inputs are lost.  That adds complexity, since you'll need 2 processes running, not 1.

I actually don't care about the test environment.  The production needs matter, since things that work in test are usually 10% of what is needed for production level code.  Getting something working with exactly perfect inputs isn't hard, but what happens for non-perfect inputs?

---

