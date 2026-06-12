---
title: "BlueFish? Nvu? Search &amp; replace inside html files"
date: 2005-09-03
forum: General Help
---

### Post by dbeckham32 on 2005-09-03
As a Windows-turned-Linux user, I need to determine how to batch replace text inside HTML files and save them. On Windows, I would simply use HomeSite's external search and replace feature.

I have NVU and BlueFish but I'm having trouble figuring out if this can be done. Please note that I'm not very fluent in regular expressions.

For example, in a directory of 100 HTML files, I would like to replace:

"text_to_replace_is_here"

with the text:

"text_to_insert_here"


Sounds simple enough. Should I use the command line? If so, how? Can BlueFish do this? If so, can I please have assistance with constructing a regular expression?

Thanks in advance!

---

### Post by mcmuffy on 2005-09-03
Spotted 'regexxer' in synaptic. The blurb says :
Regexxer is a nifty GUI search/replace tool featuring Perl-style
regular expressions. If you need project-wide substitution and you're
tired of hacking sed command lines together, then you should
definitely give it a try.

Is this the sort of thig you are looking for?

---

### Post by majikstreet on 2005-09-03
Gedit can do it.

Open Gedit in gnome (Applications--> Accessories-->Text Editor) then open your file then go to Search, then replace

Then it should be self-explainitory.

majikstreet

---

### Post by dbeckham32 on 2005-09-04
McMuffy, you are a wonderful person. Take a bow. Yes, that what I had in mind and it's working perfectly!

Thanks a million.

---

