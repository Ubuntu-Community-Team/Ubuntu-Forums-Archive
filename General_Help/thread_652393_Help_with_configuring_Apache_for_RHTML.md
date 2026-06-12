---
title: "Help with configuring Apache for RHTML"
date: 2007-12-28
forum: General Help
---

### Post by rmhartman on 2007-12-28
I am not entirely certain where this would be appropriate, so I chose "General".

I have installed the XAMPP environment (Apache, MySQL, PHP).  I have also installed Ruby.  I have configured Apache to run Ruby files, which it will as either .rb or .cgi.  So far, so good.  Now to get Apache to handle .rhtml files, we need to use the "erb" module.  This results in an "Internal Server Error" page.  It does not even have to be a .rhtml file.  Even though straight Ruby works in .rb files, if I create a .rb file that includes the line "require 'erb'" I get the same "Internal Server Error".

I am guessing this is because the erb module is located somewhere out of the Apache server directory tree.  Is there anything I an do to tweak the configuration so that it allows execution of modules not directly in the Apache tree?

-Richard M. Hartman

---

