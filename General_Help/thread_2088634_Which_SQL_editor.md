---
title: "Which SQL editor?"
date: 2012-11-27
forum: General Help
---

### Post by eUncle on 2012-11-27
Hi,

I'm looking for a SQL editor.
It should be able to highlighting / mark primary key and foreign key...

Which SQL editor do you use?



Thank you very much.

---

### Post by pkadeel on 2012-11-27
For MySQL database, mysql-workbench works fine once you get used to it.

---

### Post by eUncle on 2012-11-27
Our professor uses 'Query' on windows 7.
I'll try it.

---

### Post by codemaniac on 2012-11-27
> **eUncle said:**
> Hi,

I'm looking for a SQL editor.
It should be able to highlighting / mark primary key and foreign key...

Which SQL editor do you use?



Thank you very much.

I have been using Oracle SQLDEVELOPER happily for a long time.

---

### Post by slickymaster on 2012-11-27
I highly recommend the free [Oracle SQL Developer]("http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html"), but you also have severall alternatives you might want to look at:

[easyDBase]("http://www.beansoup.de/index.php?option=com_content&view=article&id=54&Itemid=53")
[DBVisualizer]("http://www.dbvis.com/")
[Jailer]("http://jailer.sourceforge.net/home.htm")

These are all tools supporting more than one database product.

---

### Post by eUncle on 2012-11-27
I've installed the SQL Developer via the Ubuntu Software Center. But it doesn't run.
Should look for the reason tomorrow ;)




Maybe I don't have to start a new topic: Do you can also recommend a EIFFEL editor? (need that for my study^^)


Thanks @all!



#Edit#
@slickymaster: downloading it now from oracle directly and try it this way ;)

---

### Post by slickymaster on 2012-11-27
> **eUncle said:**
> I've installed the SQL Developer via the Ubuntu Software Center. But it doesn't run.
Should look for the reason tomorrow ;)

Ensure you have a JDK installed. You can connect to and use any JDK 1.6.0_11 or above.

---

### Post by slickymaster on 2012-11-27
> **eUncle said:**
> Maybe I don't have to start a new topic: Do you can also recommend a EIFFEL editor? (need that for my study^^)


Thanks @all!





[Eclipse Eiffel Development Tools (EDT)]("http://sourceforge.net/projects/eedt/")

---

### Post by eUncle on 2012-11-27
I used eclipse for java --> sounds good :)
I've got a JDK installed. (Needed it for java.)

---

### Post by slickymaster on 2012-11-27
Did you set the $ORACLE_HOME environment variable in sqldeveloper.sh – the script that gets called to start SQLDeveloper?

---

### Post by eUncle on 2012-11-28
No, I've not set any variables.
I've only installed it via the Ubuntu Software Center.

#Edit#
Well, I've just removed it (via Ubuntu Software Center), and downloaded the rpm directly from Oracle.
Will I get a launcher icon to start this program when the rpm-file is installed?


#Edit#
I've extracted the rpm-file, move to [extractedDirectory]/opt/sqldeveloper/sqldeveloper.sh and run it in the terminal. It works.

---

### Post by slickymaster on 2012-11-28
Glad you've managed to solve it. Now you can mark this thread as solved.

Good luck with your classes.

---

### Post by eUncle on 2012-11-28
Yup! Thank you all very much for help.

---

### Post by ian magic on 2012-11-28
by the way , what is a SQL

---

### Post by slickymaster on 2012-11-28
> **ian magic said:**
> by the way , what is a SQL

SQL stands for Structured Query Language. It's a programming language designed for managing data in relational database management systems (RDBMS).

---

