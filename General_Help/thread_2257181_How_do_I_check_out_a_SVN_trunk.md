---
title: "How do I check out a SVN trunk?"
date: 2014-12-17
forum: General Help
---

### Post by Maheriano on 2014-12-17
I created a SVN repository on my server at /home/svn/web and I would like to check out the trunk of this brand new project to maintain trunk as my development copy. I created the /home/svn/web/trunk folder and then changed all the folder permissions as required in the SVN setup (mkdir trunk tags branches).
I was able to easily check out the main repository using the following:
svn co svn://computeripaddress/ .

That checks out the web repository but I'm trying to check out trunk so I run the following:
svn co svn://computeripaddress/trunk .
I get an error telling me that directory doesn't exist.

I've been able to check out trunk directories in environments set up by other people before, what do I have to do to enable this?

---

