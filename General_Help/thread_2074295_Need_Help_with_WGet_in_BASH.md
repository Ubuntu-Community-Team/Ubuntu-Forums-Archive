---
title: "Need Help with WGet in BASH"
date: 2012-10-21
forum: General Help
---

### Post by SeanKD on 2012-10-21
I'm running into a bit of a problem with wget in bash.  I thought I would put the question to the community and see if anyone can help me out.
The problem is that wget will not save to the directory specified in the -P option when I use the following code in a bash script:
```
wget -q -P $saveDIR $picURL -O $picName
```
Instead of saving the file to the save directory, the file is downloaded to the working directory of the bash script.

Any ideas what's causing this behavior?

BTW, $saveDir is set to $HOME'/Pictures/'

---

### Post by Lars Noodén on 2012-10-21
I am able to duplicate the error.  I can't get wget to pay attention to the directory prefix.  So unless we are misinterpreting how -P (--directory-prefix) is used, there might be an error with wget.

---

### Post by SeanKD on 2012-10-21
> **Lars Noodén said:**
> I am able to duplicate the error.  I can't get wget to pay attention to the directory prefix.  So unless we are misinterpreting how -P (--directory-prefix) is used, there might be an error with wget.

I don't think I'm misinterpreting -P.  For now I have gotten around the problem by saving the working directory to $workingDir then doing a cd to $savDir, executing wget without -P, and then doing a cd back to $workingDir.

Is it possible that the binary wget package for 12.10 wasn't properly compiled?

---

### Post by Lars Noodén on 2012-10-21
FWIW I just tried wget on another Linux distro and had the same problem with -P.  It may be a problem with wget, it is in the package 'wget'.  If you file a bug (ubuntu-bug wget), post the link here so we can comment.

---

### Post by sisco311 on 2012-10-21
Thread moved to **General Help.**

-O overrides the -P option. Either use -P or -O:
```
wget -P $dir $url
wget -O $dir/$name $url
```

Also -O may not work as you expect. Please check out the man page for details:
```
man wget | less +/"^ +-O file"
```

---

### Post by SeanKD on 2012-10-21
> **sisco311 said:**
> Thread moved to **General Help.**

-O overrides the -P option. Either use -P or -O:
```
wget -P $dir $url
wget -O $dir/$name $url
```

Also -O may not work as you expect. Please check out the man page for details:
```
man wget | less +/"^ +-O file"
```

Thanks for the help!!! :)

---

### Post by Lars Noodén on 2012-10-21
-P also doesn't seem to mix with -r either.  I'm not sure what the point of -P would be if it is overridden by the other options.

---

### Post by SeanKD on 2012-10-21
I decided to go with curl instead of wget in my bash script.  It seems to be less quirky and more predictable.  Thanks for the help!  At least I learned something about the -P option in wget for future reference! :)

---

