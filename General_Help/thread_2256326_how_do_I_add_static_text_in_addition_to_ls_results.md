---
title: "how do I add static text in addition to ls results when using tee command"
date: 2014-12-11
forum: General Help
---

### Post by cris7 on 2014-12-11
I'm running the following:[INDENT]ls *.dbf | tee filename
[/INDENT]

This creates a file called ***filename***, and puts the results of ***ls *.dbf*** into that file, with a separate line for each file* **ls*** returns:[INDENT]
example1.dbf
test1.dbf
here_it_is.dbf
[/INDENT]

I then go in and manually add ***~~~*** at the beginning of each line in ***filename***:

~~~example1.dbf
         ~~~test1.dbf
~~~here_it_is.dbf


Is there a way to incorporate the ***~~~*** addition into the command so that every line in ***filename*** begins with ***~~~***?

Please help, and thanks!

---

### Post by matt_symes on 2014-12-11
Hi

You could do something like this.

Move into the directory you want and type.

```
for f in *.dbf; do printf "~~~%s\n" "$f"; done > filename
```

This will not recurse into child directories.

Kind regards

---

### Post by cris7 on 2014-12-11
Thanks  				 					[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=1067998") 				 				 					 						 	[**[COLOR=#DD4814][B]matt_symes**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1067998")!


I also found that this worked...

[I][B]ls *.dbf | tee runfile | awk '$0="~~~"$0' > filename
[/B][/I]

Not sure if your example or mine really make a difference, I'm still pretty new at this.  

I did turn my example above into an executable script and will now run it whenever I need to generate the file...

Thanks again!

---

### Post by matt_symes on 2014-12-11
Hi

> **cris7 said:**
> 
Not sure if your example or mine really make a difference, I'm still pretty new at this.  


One difference is that the pipeline is slightly slower as it forks more processes and this is expensive. This can make a real difference on large datasets and depending on how you code your scripts.

For one file 

```
matthew-laptop:/home/matthew:3 % ls *.dbf
test.dbf
matthew-laptop:/home/matthew:3 
```

```
matthew-laptop:/home/matthew:3 % time ( for f in *.dbf; do printf "~~~%s\n" "$f"; done > filename )
( for f in *.dbf; do; printf "~~~%s\n" "$f"; done > filename; )  0.00s user 0.00s system 77% cpu 0.002 total
matthew-laptop:/home/matthew:3 %
```

```
time (ls *.dbf | tee runfile | awk '$0="~~~"$0' > filename)
( ls -F --color=auto *.dbf | tee runfile | awk '$0="~~~"$0' > filename; )  0.00s user 0.01s system 94% cpu 0.007 total
matthew-laptop:/home/matthew:3 %
```

However in this case the difference is so small (at least for one file), we'll ignore it :)

Obviously one would want an averaged time to get more accurate results.

Kind regards

---

