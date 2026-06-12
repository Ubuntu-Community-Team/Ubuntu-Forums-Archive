---
title: "Running .py files"
date: 2008-06-04
forum: General Help
---

### Post by webcoded612 on 2008-06-04
I'm not sure what category this goes in, so I'm sticking it here. 

I downloaded a screenlet (not Screenelets from the repositories...they're broken) and it has .py files.  I read somewhere that all you have to do is copy the screenlet files to a certain folder and run the script, so my two questions are this:

1.  What folder do they need moved to?

2.  How do I run the script?

Any help would be great.  Thanks.

---

### Post by bingoUV on 2008-06-04
> **webcoded612 said:**
> I read somewhere that all you have to do is copy the screenlet files to a certain folder and run the script

I don't know about running screenlets. The "somewhere" that you read should tell you about where to copy the files.

But for running .py files, they are most likely python. You have two options for running them :
1.
```

python filename.py

```

2. If the first line of the script is "#!/usr/bin/python", simply running it in the terminal after giving execute permissions would be enough like this
```

chmod +x filename.py
./filename.py

```

---

### Post by webcoded612 on 2008-06-04
> **bingoUV said:**
> I don't know about running screenlets. The "somewhere" that you read should tell you about where to copy the files.

But for running .py files, they are most likely python. You have two options for running them :
1.
```

python filename.py

```

2. If the first line of the script is "#!/usr/bin/python", simply running it in the terminal after giving execute permissions would be enough like this
```

chmod +x filename.py
./filename.py

```

It didn't say where to put them, and I don't remember where I read that.  So I guess I'm stuck with screenlets from the repository, eh?  I wish those things were coded to keep the settings.  If it would remember to stay on bottom and stay to the right there wouldn't be an issue with them.  

Ah well, guess it'll just be some time before they work properly.  

Thanks.

---

