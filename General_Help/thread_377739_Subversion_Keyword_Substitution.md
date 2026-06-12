---
title: "Subversion Keyword Substitution"
date: 2007-03-06
forum: General Help
---

### Post by taberski on 2007-03-06
I installed Subversion on a Ubuntu 6.06 LTS server with the intent of accessing a repository from a Window PC running Tortoise.

I have everything working fairly well using a svnserve - the only piece that I cannot get working is keyword substitution.  I set:

enable-auto-props = yes

and

*.vhd = snn:keywords=Id

under [auto-props] in /etc/subversion/config

and I included the keyword $Id$ in my test file (with a .vhd extension).

But when I add my file, commit and update the $Id$ is not expanded. 

I've been working with this for several days, I've followed a number of tutorials (including one posted on this web site) and have referenced svn-book.pdf and TortoiseSVN-1.4.3-en.pdf and am now stumped.

I'm hopeful that someone else may have worked through a similar problem and may be able to shed some light on this.

Thank you,

Kevin Taberski

---

### Post by taberski on 2007-03-08
OK - I figured it out!

I was not properly separating the functions of the Server from the Client.  Somehow, I missed the connection/separation of the two.

So here's what I learned (probably obvious to most - but may prove useful to the unenlightened ;-)

The configuration file /ect/subversion/config is the global configuration file for svn running on the Linux (Ubuntu) box.  The PC running TortoiseSVN under Windows is a separate client and it has it's own config file!  For a reason that I can't explain, this little factoid was not obvious to me and took me way longer to discover than it should - has anyone else experienced this?

Anyway, assume that you have a TortoiseSVN (TSVN) workspace set up under:

C:\somedir\SVN

In Windows Explorer, right-click on SVN, select TortoiseSVN -> Settings.

Under "General" there is a box labeled "Subversion" and a field "Subversion Configuration File:" with a button conveniently labeled "Edit" - hmmm!

Click edit, Now you edit the 'config' file just like you would edit /etc/subversion/config of your Linux PC.  In my case, uncomment "enable-auto-props=yes" and add the line:

*.vhd = svn:eol-style=native;svn:keywords=Id

I had assumed that the Server (svnserve) was accessing /etc/subversion/config and could not understand why it wasn't working - now I know!

I hope someone else may find this useful!

Kevin Taberski

---

