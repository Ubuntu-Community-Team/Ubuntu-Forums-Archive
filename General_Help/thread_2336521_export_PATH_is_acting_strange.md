---
title: "export PATH is acting strange"
date: 2016-09-09
forum: General Help
---

### Post by verber001 on 2016-09-09
Hello I'm attempting to install a graph db on my freshly installed 16.04 LTS distro.  I attempted to set the path:

```
export PATH=/dir/sub/ 
```
then realized I should've been doing (at least I think):
```
export PATH=/dir/sub:$PATH
```
now I get output like the following:

```
PATH directory '/dir/sub:" does not exist
```
when I attempt to reset the path with I get
```
bash: export '/dir/sub:=/dir/sub': not a valid identifier
```

Can someone help me out here.  I need to get rid of that path first off then set the path correct (I know it's sacreligious but it's the only thing MS makes easier is the path...imho)

Thanks all

---

### Post by Keith_Helms on 2016-09-09
Are you actually using the names "dir" and "sub" in your path?  Those are just examples.  You need to use the real path to where this graph db is located.  Once you do that, this command format should work fine (NOTE: this is JUST AN EXAMPLE)
```
export PATH="/real/path/todb:$PATH"
```

The reason you got
```

bash: export '/dir/sub:=/dir/sub': not a valid identifier
```
is probably due to doing something like this
```
export $PATH=$PATH
```
Don't use the dollar sign in front of the variable name in the export command.

If you want this directory to always be in your path and not have to enter it every time you boot, take the export line, remove the word export, and add it to the end of the .profile file in your home directory.
```
PATH="/real/path/todb:$PATH"
```

---

### Post by verber001 on 2016-09-09
_***This is just an example for all your sakes not the actual path which is simply:***_
```
**export STARDOG_HOME=/data/stardog:$STARDOG_HOME**
```
> **Keith_Helms said:**
> Are you actually using the names "dir" and "sub" in your path?  Those are just examples.  You need to use the real path to where this graph db is located.  Once you do that, this command format should work fine (NOTE: this is JUST AN EXAMPLE)
```
export PATH="/real/path/todb:$PATH"
```

_***To my knowledge that is not what I did***_
The reason you got
```
export $PATH=$PATH
```
Don't use the dollar sign in front of the variable name in the export command.


_***Yes that is my understand...this is like starting a large Teradata or Oracle system.  You turn in on and left it on.  ***_
If you want this directory to always be in your path and not have to enter it every time you boot, take the export line, remove the word export, and add it to the end of the .profile file in your home directory.
```
PATH="/real/path/todb:$PATH"
```

---

