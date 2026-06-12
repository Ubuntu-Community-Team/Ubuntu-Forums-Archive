---
title: "Pass authentication to apache via URL?"
date: 2013-08-01
forum: General Help
---

### Post by DGXJXMx on 2013-08-01
It's a great convenience to be able to access the files served up by my apache web server over the Internet but a great inconvenience and concern when I check the logs each day to see hundreds of requests by bots and indexers and god knows what else (NSA, lol) scanning all my files.

I tried the old htaccess authentication method to lock them out but that didn't seem to stop them very much so I wondered if I could slip some kind of special keyword or characters into my URL request for apache to look for when I access it, apache could then respond to requests made to it that contain this special string and reject all the ones that don't, would that be possible?

Thanks in advance :)

---

### Post by SeijiSensei on 2013-08-01
Alternatives:

1)  Use another port instead of 80.  Choose a number between 1024 and 65534.

2)  Reinstate username and password protection via .htaccess.  If you require a password, that will keep random passers-by from seeing the files.  You cannot stop the requests from arriving; you can only control whether the requests get replies.

3)  Use an Alias directive to rename the actual file location to an arbritrary string.  In the configuration file for the web site, add something like:

```

Alias   /mysecretplace /path/to/your/files
DocumentRoot /var/www

```

This returns the default "It works!" page to people who visit the / URL, but to see your files, you would need to visit [http://yourserver/mysecretplace](http://yourserver/mysecretplace).

---

### Post by DGXJXMx on 2013-08-02
Thanks for the reply, I'll have a play with it now. Will the [COLOR=#000000][FONT=Ubuntu Mono]/path/to/your/files[/FONT][/COLOR][COLOR=#000000] still be accessible the usual way at the same time?[/COLOR]

---

### Post by SeijiSensei on 2013-08-02
If by "the regular way" you mean navigating to [http://yourserver/](http://yourserver/) and seeing your files, then no.  That returns the index of the directory in the virtual host's DocumentRoot.  In the configuration I suggested that is pointed to /var/www, the default Ubuntu location.  References to the plain "/" URL will return the "It Works!" page.  You would need to visit [http://yourserver/mysecretplace](http://yourserver/mysecretplace) to see the files contained in /path/to/your/files.

If by "the regular way" you mean navigating to /path/to/my/files on the server itself, then yes that will work.  The "Alias" directive creates, well, an alias; it doesn't change anything in the local filesystem.

---

### Post by DGXJXMx on 2013-08-02
ahh yes sorry i should have been more specific, i did mean when the /server/folder/in/www was navigated to in the browser.
Thanks again, i opted for the password protected obscure ports route. worked like a charm :)

---

