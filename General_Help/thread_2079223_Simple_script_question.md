---
title: "Simple script question"
date: 2012-11-01
forum: General Help
---

### Post by Gotti on 2012-11-01
Why wouldn't the following script work? It's seemingly quite a simple string comparison script.

```
#!/bin/sh
one="foo"
if "$one" == "foo"
then
echo "It's foo!"
else
echo "It's not foo!"
fi
```

I've tried the following variations:

```
#!/bin/sh
one="foo"
if [ "$one" == "foo" ]
then
echo "It's foo!"
else
echo "It's not foo!"
fi
```

```
#!/bin/sh
one="foo"
if [[ "$one" == "foo" ]]
then
echo "It's foo!"
else
echo "It's not foo!"
fi
```

```
#!/bin/sh
one="foo"
if ( "$one" == "foo" )
then
echo "It's foo!"
else
echo "It's not foo!"
fi
```

I've also tried various combos of putting the variable's in quotes / apostrophes.

Sorry for the simple question...but I'm killing myself trying to figure out this ridonculously simple problem.

Thanks!

---

### Post by Lars Noodén on 2012-11-01
That's because the [test](http://manpages.ubuntu.com/manpages/precise/en/man1/test.1.html) for strings is just a single equal sign (=)

```

if [ "$one" = "foo" ]

```

Each language has its own quirks.

---

### Post by lykeion on 2012-11-01
```
one="foo"; if [ "$one" == "foo" ]; then echo "It's foo"; else echo "It's not foo"; fi
```

works fine

Edit:
Lars is right (too much Java for me), Bash uses single equal sign for string comparison

[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

---

### Post by Gotti on 2012-11-01
-.- Thank you! lol

I didn't even consider one '=' because I thought that was only for numerical comparisons. 

<---Noob.

---

### Post by drmrgd on 2012-11-01
Here's some more info to help you out.  Bash has a lot of (and very rigid list of) comparison / test operators:

[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

Also, Greg's Wiki is really nicely written and explains a lot of this stuff very well:

[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

---

