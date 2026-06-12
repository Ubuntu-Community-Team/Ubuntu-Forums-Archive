---
title: "Bash script errors with importing directory variable"
date: 2013-09-23
forum: General Help
---

### Post by ignisuti on 2013-09-23
I have a PARAMETERS.txt file with the following:
```
#!/bin/bash
export PATHTEST=/media/Data
```

I have a Reset_Permissions.txt file with the following:
```
#!/bin/bash
. PARAMETERS.txt

echo $PATHTEST
sudo chmod 750 -R PATHTEST
```

When I run Reset_Permissions, I get the following output:
```
/media/Data
: No such file or directoryne 5: cd: /media/Data
```

If I do away with the PARAMETERS.txt file and just stick the PATHTEST variable in my Reset_Permissions.txt file it runs without error. Why?

---

### Post by Habitual on 2013-09-23
```

#!/bin/bash
export PATHTEST=/media/Data
sudo chmod 750 -R "$PATHTEST"
```

Always [quote your variables]("http://tldp.org/LDP/abs/html/quotingvar.html").

---

### Post by ignisuti on 2013-09-24
Thanks for the response, but qouting didn't seem to help me.

---

### Post by SeijiSensei on 2013-09-24
I have some scripts where the environment variables are defined in one file and included in the script itself using the same method you show above.  However I do not use the "export" command in the file containing the definitions, nor do I start it with a "#!/bin/bash" line.  The included file just has name/value pairs and no commands.  Something like this:

file.conf
```

INPUT=/home/user/input
OUTPUT=/var/log/output.log
[etc.]

```

script:
```

#!/bin/bash
. /path/to/file.conf
[stuff]

```

---

### Post by Kissell on 2013-09-24
Habitual's right, you should always quote your variables, it's good practice, solves lots of potential problems...  but also your PATHTEST in the Reset_Permissions.txt needs a dollar sign in front of it on the chmod line, like it has on the echo line.  It won't work without that.

Also, the file you're calling needs to be marked as executable.  After you created PARAMETERS.txt you need to run "chmod +x PARAMETERS.txt" on it.

---

### Post by ignisuti on 2013-09-24
I've emulated your suggestions as closly as possible and still no joy. 

I was seeing a couple errors when I posted this. The actual error to focus on is as follows:
```
chmod: cannot access @/media/Data\r@: No such file or directory
```
The @ symbols are actually an 'a' character with a '^' symbol above it.

So, looks to me like there's an extra carriage return stuck at the end, but I'm not sure how to clean that up.

---

### Post by Kissell on 2013-09-24
Also, environment variables can have a scope of the user that set them.  

When you're using "export" it's running as your user, but when you run "sudo chmod" it's running as the root user.  

Maybe your variable isn't being set for the root user.

---

### Post by Kissell on 2013-09-24
I copied your code from the original post and made the files with the same filenames then ran "chmod +x *.txt" to make them both executable and changed the PATHTEST to "$PATHTEST" then ran it, and it worked fine.

There must have some weird hidden character in your files somehow...  just delete your files and recreate them like I did by copying them out of your original post.

---

### Post by ignisuti on 2013-09-24
> **Kissell said:**
> 
There must have some weird hidden character in your files somehow...  just delete your files and recreate them like I did by copying them out of your original post.

Huh?!? Kissell, you solved my problem! Thanks!
I have no idea how that happened...

A thousand blessings on you and your family!!!

---

