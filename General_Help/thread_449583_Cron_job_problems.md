---
title: "Cron job problems"
date: 2007-05-20
forum: General Help
---

### Post by Dave Smith on 2007-05-20
I'm using a dedicated server running Ubuntu and have three Drupal based web sites running.

On each of these sites I am running a cron job to update news. On two of the sites the cron job works OK but on the third, for some obscure reason, it is not running at all. Apart from a the different URL, the script is the same for all sites:

**/15 * * * * /usr/bin/wget -O- -q /dev/null [http://mysite.org/cron.php](http://mysite.org/cron.php)*

I am presuming that the 'O' is an 'o' and not a zero ('0').

Does any one have any ideas?

Thanks

Dave Smith

---

### Post by mbradlcu on 2007-05-21
I'm not exactly sure what you're doing with wget but this may be of interest:
is the "-O-" a typo and you meant "-O"?

```
wget -O- -q /dev/null http://mysite.org/cron.php
```
returns nothing.

```
wget -O  -q /dev/null http://mysite.org/cron.php
```
returns:
/dev/null: Unsupported scheme.
--00:05:14--  [http://mysite.org/cron.php](http://mysite.org/cron.php)
           => `-q'
Resolving mysite.org... 207.114.175.50
Connecting to mysite.org|207.114.175.50|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
00:05:14 ERROR 404: Not Found.

---

### Post by asipi on 2007-05-21
it means wget -O - URL
but why is it useful to get the result onto STDOUT?
cron starts the command in the background so you won't be able to see it...
or am I wrong?

---

### Post by Dave Smith on 2007-05-21
Thanks for your prompt response.

The "-O-" was not a typo but I have changed all three cron jobs to "-O". It hasn't changed anything in the sense that two of the cron jobs are working (as they were before) and the same one is not.

Any other ideas?

---

### Post by kh4nh on 2007-05-21
> **Dave Smith said:**
> 
**/15 * * * * /usr/bin/wget -O- -q /dev/null [http://mysite.org/cron.php](http://mysite.org/cron.php)*


-O switch is to output, /dev/null is the file the command outputs to. Try this:

```
**/15 * * * * /usr/bin/wget -q -O /dev/null [http://mysite.org/cron.php](http://mysite.org/cron.php)*
```

---

