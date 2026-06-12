---
title: "Microsoft Enterprise Manager on Linux"
date: 2007-01-24
forum: General Help
---

### Post by Devilotx on 2007-01-24
the last tool on windows that I need for work, is Microsoft enterprise Manager, is basically a GUI for accessing Microsoft SQL databases to make manual edits and changes in a GUI.

it also comes with SQL Query Analyzer.

this is the last thing I need, something gui based that can read and make changes to a MS SQL database.  I see lots that hit MySQL, is there anything to fill this role?

---

### Post by matthewstory on 2007-01-24
i did a google search for "web MSSQL admin" it returned many results for web-based administrative tools for MSSQL like phpMyAdmin for MySQL.  Two that looked good:

[http://www.mylittletools.net/scripts/en/mla_sql/](http://www.mylittletools.net/scripts/en/mla_sql/)

and also ciberadmin, which claims to work for MSSQL MySQL and PostgreSQL.

Though, these web-based tools tend to be quite vulnerable to security risk and attacks.  Out of curiousity, why don't you just switch to PostgreSQL or MySQL, they are both superior to MSSQL imho, and the support for them on Linux is remarkable.

If neither of these work, you could also just install WINE.

cheers

---

### Post by marianom on 2007-01-24
It seems Oracle's free [Sql developer]("http://www.oracle.com/technology/products/database/sql_developer/index.html") can access MSSql databases too. Sure not to the extend od MSSQL EM (you won't find that kind of stuff in linux) but maybe you can try it.

---

### Post by Devilotx on 2007-01-25
> **matthewstory said:**
> i did a google search for "web MSSQL admin" it returned many results for web-based administrative tools for MSSQL like phpMyAdmin for MySQL.  Two that looked good:

[http://www.mylittletools.net/scripts/en/mla_sql/](http://www.mylittletools.net/scripts/en/mla_sql/)

and also ciberadmin, which claims to work for MSSQL MySQL and PostgreSQL.

Though, these web-based tools tend to be quite vulnerable to security risk and attacks.  Out of curiousity, why don't you just switch to PostgreSQL or MySQL, they are both superior to MSSQL imho, and the support for them on Linux is remarkable.

If neither of these work, you could also just install WINE.

cheers

the company I work for is a "Microsoft" shop, so to speak.  I've worked on adding linux into a few sectors (our DNS servers, FTP servers and one mail server) and I'd prefer to work in linux myself.  since the applications we write all use MSSQL, I'm stuck.  there is no way I can convince 20+ Web Developers to move to a new platform.

---

### Post by dcstar on 2007-01-25
> **Devilotx said:**
> the company I work for is a "Microsoft" shop, so to speak.  I've worked on adding linux into a few sectors (our DNS servers, FTP servers and one mail server) and I'd prefer to work in linux myself.  since the applications we write all use MSSQL, I'm stuck.  there is no way I can convince 20+ Web Developers to move to a new platform.

If you have servers running Microsoft SQL server then simply use your Linux desktop to RDP into those servers and use the tool there.

---

### Post by Devilotx on 2007-01-25
yeah, that's what I've been doing, I was just wondering if there was a native tool.

---

### Post by EricWiz on 2007-06-11
I just started using SQuirrel client. Admittedly only on windoze now, but I will be adding it to my ubuntu box at home in the next day or two.  It is a java client so its cross-platform. This was the last piece I need (I think) to kiss windoze good bye!

Check it out here:
[Squirrel Client]("http://squirrel-sql.sourceforge.net/")

Eric

---

