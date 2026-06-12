---
title: "Blogging Software Recommendations?"
date: 2020-08-14
forum: General Help
---

### Post by mokane324 on 2020-08-14
Drivel is gone. Blogilo is gone. Bloxsom? No installation candidate. 
Once upon a time, maybe a decade ago, there were all sorts of blogging programs. 
Not any more.
Static sight generators are popular, but to make a single post you have to:
--write post
--run generator
--ftp your post.
That's three separate programs. So a static site generator isn't the solution.
Is there any program like the Drivel, Blogilo, Live Writer (Windows) for Ubuntu?
Supposedly there was something called Gnome Blog but I can't find it.

---

### Post by CelticWarrior on 2020-08-14
Welcome.

Bloxsom: [http://blosxom.sourceforge.net/documentation/users/install/dynamic/isp.html](http://blosxom.sourceforge.net/documentation/users/install/dynamic/isp.html)

Other ideas: [https://www.ubuntupit.com/best-blogging-software-for-linux/](https://www.ubuntupit.com/best-blogging-software-for-linux/)

---

### Post by mokane324 on 2020-08-14
Bloxsom is now Flatpress, flatpress.org.
I came across that article, it is more about engines than clients and is already outdated (see the comments to the article).

And not really "welcome," lost my earlier login.

---

### Post by TheFu on 2020-08-14
Static generators ARE the answer.

Nobody should be using plain FTP since 2002-ish.  Use rsync over an ssh connection. That's the default for rsync.

Running the generator and running **rsync** when **ssh-keys** have been setup can be automated.

To generate stuff, I use a Makefile, but a trivial script can do it too.

Of course, lots of people use complex blogging systems that require logins and get hacked.  Wordpress is one of those. I have an old Publify instance running, but have added so many added protections to prevent hacking access, it isn't funny. Took years.  I really need to migrate to a **webgen** static blog or a **Template::Toolkit** version. My blog has over 2,000 articles, so I'd like to migrate those AND all the comments. That's been the hardest part and why the migration isn't done.  

Whatever you select, think about 5 yrs from now when you want to migrate to a new solution.

---

### Post by mokane324 on 2020-08-14
@TheFu. The problem with a static generator is that you can't just write and post. There are too many hoops to go through after you create a post. If Ghost wasn't so expensive or I could self-host, I'd do that.

---

### Post by SeijiSensei on 2020-08-15
What's wrong with WordPress? You can have a free blog at [https://wordpress.com/create-blog/](https://wordpress.com/create-blog/).

Or you can rent an entire virtual server at [Linode for $5/month]("https://www.linode.com/pricing/") and install Apache+WordPress there.

The former is easier since you don't have to install updates. The latter gives you a lot more flexibility than just running a blog.

---

### Post by HermanAB on 2020-08-16
Google Blogger costs nothing and it works.  This is probably why most other blog writing utilities faltered.

BTW, Writing and Publishing to a static site is only two steps if you don't know how to make a one line script.

---

