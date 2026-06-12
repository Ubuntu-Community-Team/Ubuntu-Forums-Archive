---
title: "php request_uri"
date: 2007-01-19
forum: General Help
---

### Post by Ubuntuud on 2007-01-19
Hi,

I will get right to the point.
How can your request an url _without_ the $_GET variables?
$_SERVER['REQUEST_URI'] does not work, since it includes those variables.
So when I am visiting 'http://localhost/index.php?var=anoying'. I want a command that returns 'index.php', or 'http://localhost/index.php'.
Is this even possible?
Thanks in advance!

---

### Post by mssever on 2007-01-19
> **Ubuntuud said:**
> Hi,

I will get right to the point.
How can your request an url _without_ the $_GET variables?
$_SERVER['REQUEST_URI'] does not work, since it includes those variables.
So when I am visiting 'http://localhost/index.php?var=anoying'. I want a command that returns 'index.php', or 'http://localhost/index.php'.
Is this even possible?
Thanks in advance!

One way would be to do something like [php]substr(0,strpos($_SERVER['REQUEST_URI'], "?"));[/php]

---

### Post by JamieC on 2007-01-19
Why don't you just use the PHP_SELF key?

---

### Post by Ubuntuud on 2007-01-19
Thanks you both...
Right now I will use mssever's solution.

But JamieC, I'm rather new to PHP, what exactly is the PHP_SELF key?
I should have followed a tutorial...

---

### Post by mssever on 2007-01-19
> **Ubuntuud said:**
> Thanks you both...
Right now I will use mssever's solution.

But JamieC, I'm rather new to PHP, what exactly is the PHP_SELF key?
I should have followed a tutorial...

[quote=http://hoohoo.ncsa.uiuc.edu/cgi/env.html]'PHP_SELF'

The filename of the currently executing script, relative to the document root. For instance,                  
           $_SERVER['PHP_SELF'] in a script at the address [http://example.com/test.php/foo.bar](http://example.com/test.php/foo.bar) would be                    
           /test.php/foo.bar. The __FILE__ constant contains the full path and filename of the current (i.e. included)     
           file.[/quote]
For simple setups, PHP_SELF is the easier option. I forgot about it in my reply. But in more advanced situations, you might need something more like my solution above. For example, I use Apache's mod_rewrite extensively, to the point where my URLs often bear little to no resemblance to the actual filesystem. In that case, PHP_SELF would be meaningless.

---

### Post by JamieC on 2007-01-20
That's true mssever, but you're code is incorrect anyway.

The substr() function takes three parameters, they are string, start, and length. Therefore, the corrected code would be:
```

substr($_SERVER['REQUEST_URI'], 0, strpos($_SERVER['REQUEST_URI'], '?'));  

```

There are so many ways to do it, you could use explode() to create an array where the first key is the URL before the question mark, parse_url() to break the URL into several components (and then rebuild a URL string) or even str_replace() to replace the query string with nothing in the requested URL.

At the moment, if your script is simple and does not involve rewrites or redirects, includes or the such, PHP_SELF would be your best bet.

---

### Post by mssever on 2007-01-20
> **JamieC said:**
> That's true mssever, but you're code is incorrect anyway.

Oops. Thanks for catching that.

---

