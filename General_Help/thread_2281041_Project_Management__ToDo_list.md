---
title: "Project Management / ToDo list"
date: 2015-06-04
forum: General Help
---

### Post by Andrew_Murdoch on 2015-06-04
Hey Guys

I'm currently looking for a web based application that would allow one of my employees to login, make a project, make requirements, milestones and etc.. for that project and then assign it to me.  I'm working for three companies right now and one of the is very much part time.  I would love to find a good little web based app to help that employer, track and assign me work. 

This would ideally run on Ubuntu Server, but I do have KVM available.

Any ideas?

thanks

Docmur

---

### Post by TheFu on 2015-06-04
Redmine, sadly it is non-trivial to install and you really need to force a VPN to be used for access if you care at all about security. That applies to all project management tools that I know. Put it on a dedicated VM, since you'll want to upgrade the stack running it very carefully over the years. The version in the repos is very old and it still requires manual setup. If you know RoR already, doing the install from the current stable release isn't too hard.  Expect about 4 hrs to learn and install the first time.

I've been running redmine for about 4 yrs. Tried 3 other tools before it. None were as complete and easy to use as Redmine.  Some Fortune50 companies use Redmine for parts of their internal project management, BTW. It really is a nice tool.

For a one-man shop, I'd be inclined to go with a spreadsheet and use the GTD method. You can automate posting the top 10-50 active issues on a website for each client and they can email updates. That would be much easier.

Or Trac - [http://trac.edgewall.org/](http://trac.edgewall.org/) - not really project management. Just bug / ticket stuff.

Or you can subscribe to [Basecamp]("https://basecamp.com/"), but they are really proud of their offering.

---

### Post by tgalati4 on 2015-06-04
I've used [Tracks]("http://www.getontracks.org/") for smaller projects.  Less of a learning curve and easier to get going.  Uses the GTD paradigm which some folks have difficulty grasping and implementing.  There is a one-button (almost) installer: [https://bitnami.com/stack/tracks](https://bitnami.com/stack/tracks)

Browse through these apps and see if there is something worth implementing:  [https://bitnami.com/stacks/project-management](https://bitnami.com/stacks/project-management)

---

### Post by TheFu on 2015-06-04
I need to try out Tracks.  Nice pointer.  I keep going back to a multi-tabbed spreadsheet that folds up nicely after printing for pocket use. [http://www.pocketmod.com/](http://www.pocketmod.com/)  Usually only need to print it out when on travel and disconnected.

BTW, Redmine has a free Android client ... which can be nice.

---

### Post by tgalati4 on 2015-06-04
Tracks is pre-Android, but you can generate project action items and with a little scripting put them into your pocketmods or email them to your smartphone.

---

### Post by Andrew_Murdoch on 2015-06-05
Awesome :-), I'll check them out.

---

