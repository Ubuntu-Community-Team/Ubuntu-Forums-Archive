---
title: "Don't know where to start"
date: 2007-01-22
forum: General Help
---

### Post by edlentz on 2007-01-22
I have an idea and not sure how to get the first part operating.  I want to connect to a serial port on a phone system.  Said serial port will output a specific amount of information.  This info will always be in the same format.  There will always be a cr after the line is sent.  What I want to do is take this stream and enter it into a Mysql DB.  So, any suggestion where I can get this started?  I want to use Ubuntu.

Thanks for any direction you can help me with.

Ed

---

### Post by Wim Sturkenboom on 2007-01-23
A comment first:
unless this is an inherent part of a larger database system, the MySQL database sounds like total overkill for this (you only have one table).

How many different commands are we talking about? If it's just a few, you can store them in a normal file (so called *flat file*). If it's a lot of commands, you can consider the SqLite database.

In any case, you have to write a program (gui or text based) that opens the serial port and configures it, presents the user with the available commands, sends the selected command and handles replies (if any) and at the end of the day closes the serial port.

The choice of the programming/scripting language is yours. Just check that an 'interface' (API) as available for the database system that you decide to use (not applicable for flat file).

Once that decision is made, write some building blocks and get them working. At the end, glue them together to a final program.

---

