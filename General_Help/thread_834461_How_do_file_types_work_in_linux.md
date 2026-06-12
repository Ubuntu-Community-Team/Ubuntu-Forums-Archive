---
title: "How do file types work in linux?"
date: 2008-06-19
forum: General Help
---

### Post by Zenze on 2008-06-19
I did some searching around but all I could find related to the subject were many people talking about how linux doesnt use file extensions like windows does. However, nobody seems to say exactly how linux does figure out what to do with files. How does it know what to open a file with or how to run it?

Thanks.

---

### Post by sdennie on 2008-06-19
Check: [http://en.wikipedia.org/wiki/Magic_number_(programming)#Magic_numbers_in_files](http://en.wikipedia.org/wiki/Magic_number_(programming)#Magic_numbers_in_files)

---

### Post by Zenze on 2008-06-19
> **vor said:**
> Check: [http://en.wikipedia.org/wiki/Magic_number_(programming)#Magic_numbers_in_files](http://en.wikipedia.org/wiki/Magic_number_(programming)#Magic_numbers_in_files)

Ok cool I see.

I noticed that all script files seem to start with "#!/bin/bash" and I take that it means to run in the bash shell right? Well would that work with any file? As in putting #! followed the path to the program you want to open that file with.

---

### Post by sdennie on 2008-06-19
That's correct.  Check: [http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))

---

