---
title: "MS Sql Server Management Studio"
date: 2008-05-07
forum: General Help
---

### Post by decromos on 2008-05-07
Has anyone been able to get the 2005 Microsoft Sql Server Management Studio to load in Wine?  I'm getting this install error "Failed to load SqlSpars.dll"

Any help would be appreciated.  I'm running Ubuntu 7.04 and wine-0.9.59.

I was able to get Office 2007 loaded successfully but can't seem to get this one down.

---

### Post by wujtehacjusz on 2008-06-11
It looks like Msc SQL Server Managment Studio doesn't work in Wine (even if you manage to install it...). I would suggest some alternative software.

---

### Post by hsteckylf on 2009-04-21
Does anyone have any SQL Server 2005 Management Studio alternative suggestions? I am really trying to drop Windows completely on my laptop, but this interface with our production SQL Servers is a requirement.

---

### Post by x001 on 2009-05-14
I am in the same boat. So far I found the following:

[RazorSQL]("http://www.razorsql.com/")
[AquaData]("http://www.aquafold.com/")

Will be trying out those packages or just running WinXP through VB or VMWare and installing MS SSMS.

---

### Post by platinumriver on 2009-05-15
DB Visualizer [http://www.dbvis.com/](http://www.dbvis.com/) is also an awesome product. Since it is written in Java, it'll run fine on Linux. However, if you are managing SQL Servers and you need to control the SQL Server Agents, doing it through SSMS is much easier. I haven't found 3rd party tools yet that allow you to control the Agents.

---

### Post by Loyd Gravitt on 2009-07-09
If you do not need the GUI portion of SSMS, you can run just about any T-SQL from ubuntu using freetds.   It is open source and works great for running routine agent-like tasks from linux utilizing cron.  Freetds also works well a sybase based variant of SQL command line called sqsh which will let you write some fairly sophisticated sql scripts containing flow control logic.  I am still researching this.

---

### Post by z-itou16 on 2010-08-05
dbvisualizer made my day. Great tool now I can query to my db's without having to rdp to my server. 

Works perfect!!!

---

### Post by platinumriver on 2010-08-11
DB Visualizer has come a long way, it now has some nice management capabilities built-in. Also check out DBSolo, a very powerful SQL Query tool that runs on all platforms. DB Solo [http://www.dbsolo.com/]("http://www.dbsolo.com/") has some incredible data and schema comparisons tools built-in. You can run two separate queries, then compare the result sets. It keeps a history of your execution times, which is very helpful when you fine tune something. It has a max number of records threshold set so you don't accidentally return more than X number of rows. Good stuff.

---

### Post by rucadulu on 2012-06-01
**[SIZE=2]I use Oracle SQL Developer it is java based and works great for connecting to a SQLServer Database.[/SIZE]**

The following setup is from the below url. 
**[[SIZE=2]http://thinkoracle.blogspot.com/2010/09/using-oracle-sql-developer-with-ms-sql.html[/SIZE]]("http://thinkoracle.blogspot.com/2010/09/using-oracle-sql-developer-with-ms-sql.html")**

**[SIZE=2]Using Oracle SQL Developer with Micorsoft SQL Server.[/SIZE]**

[SIZE=2][/SIZE]
[SIZE=2]Having chosen Oracle SQL Developer as your preferred Oracle database tool, do you have to install and learn a new technology for supporting your MS SQL databases? Nope! It's easy to connect SQL Developer to MS SQL databases, and I'll show you how.

**Background**

For years I worked in technical support for software vendors, and I never knew what client tool would be available when I accessed a customer system. In fact, in many cases they'd only give me command-line SQLPlus access. Consequently I never really chose a preferred Oracle client, nor became particularly proficient with anything other than command-line SQLPlus.

Eventually I found myself working directly with a client, and could finally choose whichever tool I liked best, and like many of you I chose Raptor - now known as [/SIZE][[SIZE=2][COLOR=#b4445c]Oracle SQL Developer[/COLOR][/SIZE]]("http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html")[SIZE=2]. Explaining my choice is outside the scope of this article, but suffice it to say that it's a powerful time-saver at best, and a big step up on command-line SQLPLus at worst.

**Connecting to MS SQL**

Not all the database applications we support are going to be Oracle-based, and the most popular of the alternatives is Sybase's curious nephew MS-SQL. Fortunately there's no need to find another application for your MS-SQL instances, you can still use SQL Developer, and here's how.

**Step 1. Get the JDBC driver for MS SQL**

If you don't already have one, download a JDBC driver for MS-SQL. I use the [/SIZE][[SIZE=2][COLOR=#b4445c]jTDS driver[/COLOR][/SIZE]]("http://jtds.sourceforge.net/")[SIZE=2], which is open-source Java. It doesn't matter where you place it, but remember where.

**Step 2. Load the JDBC driver**

As explained in [/SIZE][[SIZE=2][COLOR=#b4445c]Oracle's tutorial[/COLOR][/SIZE]]("http://www.oracle.com/technetwork/developer-tools/sql-developer/thirdparty-095608.html")[SIZE=2], under Preferences, scroll down to Database and Third Party JDBC Drivers. Once you load the jtds-1.2 jar file you should see both SQL Server and it's aging uncle Sybase added to your list of options when creating a new database connection (You get Oracle and Access by default).
[/SIZE][[SIZE=2][IMG]http://1.bp.blogspot.com/_hoghde2FwwU/TIZl_ZRznfI/AAAAAAAAAxY/0aHKqoX2cgw/s320/3rdparty.jpg[/IMG][/SIZE]]("http://1.bp.blogspot.com/_hoghde2FwwU/TIZl_ZRznfI/AAAAAAAAAxY/0aHKqoX2cgw/s1600/3rdparty.jpg")
[SIZE=2]**Step 3. Set up your new database connection**

Now you can create a new MS SQL database connection the same you would an Oracle connection. The only difference is that you need to select the SQLServer tab instead of Oracle. If you don't see that tab, then something went wrong - either you got the wrong jar file or it didn't load correctly.[/SIZE][[SIZE=2][IMG]http://2.bp.blogspot.com/_hoghde2FwwU/TIZmq1s-_VI/AAAAAAAAAxg/SfnAu-vU8Bk/s320/newdb.jpg[/IMG][/SIZE]]("http://2.bp.blogspot.com/_hoghde2FwwU/TIZmq1s-_VI/AAAAAAAAAxg/SfnAu-vU8Bk/s1600/newdb.jpg")
[SIZE=2]If you're brand new to Oracle SQL Developer, [/SIZE][[SIZE=2][COLOR=#b4445c]Anders Andreasen[/COLOR][/SIZE]]("http://aandreasen.wordpress.com/2010/04/06/using-oracle-sql-developer-as-a-gui-front-end-for-ms-sql-server/")[SIZE=2] has an example with a few extra screenshots.

Use the Test button to make sure you can connect, and if you can't the error message ought to be descriptive enough to give you a starting point to troubleshoot.

**Troubleshooting**

Needless to say, technologies as complex as these will occasionally present you with unexpected difficulties. 

For instance, you may find that you need to copy the ntlmauth.dll file from the SSO directory to SQL Developer's jdk/jre/bin directory.

Or, you may need to check the Configuration Manager on your SQL Server database to make sure you have TCP/IP communication enabled, and over default port 1433.

If you used the driver I recommended, they have a [/SIZE][[SIZE=2][COLOR=#b4445c]FAQ[/COLOR][/SIZE]]("http://jtds.sourceforge.net/faq.html")[SIZE=2] that can help you track down some types of errors.

**Recap**

If you support multiple databases, there may not be a need to install multiple tools. Oracle SQL Developer can be used to connect to different flavours of databases, including MS SQL. Just download and load in the JDBC driver, and you should be able to create a new database connection as easily as you can with Oracle. [/SIZE]

[SIZE=2]// posted by Robert Vollman @ [/SIZE][[SIZE=2][COLOR=#935781]Tuesday, September 07, 2010[/COLOR][/SIZE]]("http://thinkoracle.blogspot.com/2010/09/using-oracle-sql-developer-with-ms-sql.html")

---

### Post by oldos2er on 2012-06-01
Closed. Please don't bump old threads.

---

