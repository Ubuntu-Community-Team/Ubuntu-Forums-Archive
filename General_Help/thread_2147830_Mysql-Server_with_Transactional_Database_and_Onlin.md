---
title: "Mysql-Server with Transactional Database and Online Transactions Processing (OLTP)"
date: 2013-05-23
forum: General Help
---

### Post by ngblume on 2013-05-23
Hey everyone,

this might be a rather simple question, but I couldn't find answers for hours..
I'm trying to install "opentaps" for development on an ubuntu server 12.04 LTS following this tutorial:
[http://www.opentaps.org/docs/index.php/Using_opentaps_ERP_%2B_CRM_with_MySQL](http://www.opentaps.org/docs/index.php/Using_opentaps_ERP_%2B_CRM_with_MySQL)

I'm not completely new to ubunutu and linux and servers, but I can find a way to ensure those two options for the mysql server as required in the tutorial:
> Install MySQL using the binary installation files from the [MySQL download site]("http://dev.mysql.com/downloads/"). Select "Transactional Database" and "Online Transaction Processing (OLTP)" so that MySQL will use the right database engine which would support transactions and foreign-key constraints, which are critical for an ERP/CRM application.

My current installation of mysql in ubuntu utilized apt-get and as far as i can tell allows 151 connections (acc. mysqltuner) and utilizes InnoDB.
During the installation of mysql on windows machines, the user gets to choose between these options like shown here:
[http://www.serverintellect.com/support/mysql/mysql-install.aspx](http://www.serverintellect.com/support/mysql/mysql-install.aspx) (search for "Multifunctional Database" for the Transactional Database and search for "Online Transaction Processing" for the OLTP)

Is there any way to force these options on ubuntu or are they automatically chosen...?
As far as I can tell from the infos in those screenshots, those options only select InnoDB (for transactional database) and increase the number of maximum concurrent connections to 500 (OLTP)..

Any help or clarification would be greatly appreciated !!

Kind regards
Niels Göran

---

