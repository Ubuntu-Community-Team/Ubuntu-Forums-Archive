---
title: "localhost throwing error message"
date: 2008-05-26
forum: General Help
---

### Post by mamboze on 2008-05-26
I got a problem with a rails tutorial app  in the RailsSpace book. When I run [http://localhost:3000](http://localhost:3000), and check 'your application's environment', I get error messages. 
like this:
CGI::Session::CookieStore::TamperedWithCookie in Rails/infoController#properties 
or  this:
 Mysql::Error in Rails/infoController#properties
#28000Access denied for user 'root'@'localhost' (using password: NO

The strange thing is that a tutorial app I was working on some weeks ago is  OK. checking the environment today gives

Ruby version	1.8.6 (i486-linux)
RubyGems version	1.1.1
Rails version	2.0.2
Active Record version	2.0.2
Action Pack version	2.0.2
Active Resource version	2.0.2
Action Mailer version	2.0.2
Active Support version	2.0.2
Application root	/home/roy/railsapps/shovell
Environment	development
Database adapter	mysql
Database schema version	4

The mySQL server is running OK  I can access the dbs and their data. 

I read on another site that rails 2 has sqlite3 as the default db instead of mysql and so on the command line  'rails -d mysql <app_name>' is required to set up the app framework instead of 'rails <app_name>.  
I tried it but it didn't work. I'm at a loss as to why this might be happening now rather than before. The only thing that's changed is the OS, Ubuntu 7.10 upgraded to 8.04
I wondering whether the upgrade broke something. But then why does the older tut app work? I'm lost for an answer. Needless to say, I'm on a steep learning curve here.   

Any help would be much appreciated.

---

