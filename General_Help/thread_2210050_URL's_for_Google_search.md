---
title: "URL's for Google search"
date: 2014-03-08
forum: General Help
---

### Post by Langstracht on 2014-03-08
If you do a "manual" google search

e.g search for clegg on site:bbc.co.uk  and then use the pull downs to limit the time frame you might end up with a url that looks like this:

```
https://www.google.com/webhp#q=clegg+site:bbc.co.uk&tbs=qdr:h
```

I would have then thought that using this:

```
google-chrome https://www.google.com/webhp#q=clegg+site:bbc.co.uk&tbs=qdr:h
```

as a CLI would give the same result.

I don't know what's going on but it does not.  The resulting url is:

```
https://www.google.com/webhp#q=clegg+site:bbc.co.uk
```

with the time factor absent.

Anyone know how to overcome this?

TIA

---

### Post by CaptainMark on 2014-03-08
The ampersand symbol ( & ) is a special character to the shell, you simply have to escape it with a backslash and your command will work as if you'd punched that url directly into chrome, ```
[COLOR=#000000][FONT=Ubuntu Mono]google-chrome https://www.google.com/webhp#q=clegg+site:bbc.co.uk\&tbs=qdr:h[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]I assume this is what you want to do

Although if you're that desperate to know what Clegg has been doing in the last hour, you need to find a new hobby

---

### Post by Langstracht on 2014-03-09
Thanks for the fix.  I should have known ... but that particular synapse didn't fire.

As for Clegg - he was just a recognizable "current" example.  Better I thought than "whirling dervish" on ukrinform.ua.  But that's another story ...

Thanks for your response.

---

