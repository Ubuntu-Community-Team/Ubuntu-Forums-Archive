---
title: "&quot;Global&quot; commands? [Resolved]"
date: 2007-02-22
forum: General Help
---

### Post by Gibbs on 2007-02-22
I'm unsure of the correct word/terms so I apologise as it makes it difficult for me to search about this.

I know how to use and create environment variables but what are these "global" commands?

For example nano, pico, gedit etc.Where are they stored and defined? How can I create my own? Where can I get a full list of them?

Any help appreciated and thanks.

---

### Post by llamakc on 2007-02-22
Many program executables exist in /usr/bin. You can add your own anywhere you want, but for the sake of not mucking stuff up, choose to use /usr/local/bin (you would use sudo to put them there) or in ~/bin (that means /home/YOU/bin) if you add ~/bin to your PATH.

Once your shell (most likely BASH) is aware of your added path, you would be able to use tab-completion to call the script/program without using its entire path.

One makes a script executable by doing `chmod +x nameofscript` also.

---

### Post by Gibbs on 2007-02-22
Thanks for that :)

---

