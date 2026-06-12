---
title: "need help with sbackup.  need a regular expression regex to exclude new hardy trash"
date: 2008-06-17
forum: General Help
---

### Post by kraymore on 2008-06-17
I am trying to configure sbackup to exclude my home users trash directory.  i need to do this through a "regular expression"  or regex and the example it gives is 

/home/[^/]+?/\.Trash

i am unsure if this is correct for hardy heron.  could anyone tell me what expression to add ?

---

### Post by VMC on 2008-06-17
> **kraymore said:**
> I am trying to configure sbackup to exclude my home users trash directory.  i need to do this through a "regular expression"  or regex and the example it gives is 

/home/[^/]+?/\.Trash

i am unsure if this is correct for hardy heron.  could anyone tell me what expression to add ?

I don't think it will work. For example my Trash is:
/home/vmc/.local/share/Trash

It doesn't see the ".directory"

And the ".local" fails. You can check this or any RegEx here:
[http://www.nvcc.edu/home/drodgers/CEU/Resources/test_regexp.asp](http://www.nvcc.edu/home/drodgers/CEU/Resources/test_regexp.asp)
Then you can find the right combination that works.

---

### Post by kraymore on 2008-06-17
well the regular expression that i listed was one i had taken from the default sbackup configuration.  it includes a directory started off with a . (.Trash)  so, i'm thinking that sbackup will see directories starting with dots just so long as the rest of the regular expression is correct. 

i just don't know what the correct regular expression for hardy is given the regex form i used in the example, i'm guessing, before the .Trash folder changed places on the ~/ directory with hardy.  can anyone tell me what that regular expression is ?

---

