---
title: "How to force cron to execute script in bash?"
date: 2007-07-03
forum: General Help
---

### Post by trgreerca on 2007-07-03
I have a shell script that I'd like to run every thirty minutes using cron.  

However, the scripts employs array variables that the Bourne shell does not support.  

When I execute the script from the command line it runs fine.  But, when I run it via cron, it errors out complaining about the array assignment.

How do I force cron to use bash when running this script?  

BTW, the header of the script contains #!/bin/bash.

---

### Post by PaulFr on 2007-07-03
1. Please check that **#!/bin/bash** is on the _first line_ and there are no blanks or tabs preceding it.
2. If you want some environment variables that are defined in your .bashrc or /etc/profile (i.e. those that would be defined when you login), then the _first line_ should read **#!/bin/bash -l**.
3. Please check that the file itself is executable (i.e. **chmod +x <script_file_path>**).
4. If it still does not work, then a simple test to show you what is happening would be to run **sh -x <script_file_path>** and see if the problem is in the startup of bash.
5. If it still does not give you any clues, I would suggest you change the first line to **#!/bin/bash -x** or **#!/bin/bash -l -x** as appropriate to see what is happening inside of the script, and let **cron** run the script. You should receive an email showing how the bash script was executed.
Hope this helps.

---

### Post by trgreerca on 2007-07-03
"1. Please check that #!/bin/bash is on the first line and there are no blanks or tabs preceding it."

I have a comment line as the first line.  That should be easy to fix.  

Thanks!

---

