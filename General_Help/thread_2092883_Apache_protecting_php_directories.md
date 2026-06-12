---
title: "Apache protecting php directories"
date: 2012-12-09
forum: General Help
---

### Post by [pl]ice on 2012-12-09
Hi there,

i have started using mollify through apache. Mollify is basically php scripts that enables user to login and download/upload files.
The folder structure is:
/var/www/mollify/index.html
/var/www/mollify/client  // php scripts
/var/www/mollify/backend  // php scripts

I would like to block access to client and backend (and deeper) to anybody who will enter www path for /var/www/mollify/client into web browser,
but I still need to give enough access for the user to log in and call the php from backed and client when they enter /var/www/mollify/index.html

I have played with the file premissions ,but i can't get anywhere.

Also i have put:
<Directory /var/www/mollify/client>
        <FilesMatch "\.(php3?|phtml)$">  
                 Order Deny,Allow
                 Deny from All
     </FilesMatch>
</Directory>

and that blocks the /var/www/mollify/client access from browser (and mollify fully works)

but trying to put that for /var/www/mollify/backend blocks whole mollify.

- I know i can switch off indexing but that's not the full answer.

can someone pls give me a hand with that?

thank you

mike

---

### Post by SeijiSensei on 2012-12-09
If you can alter index.html (or more likely index.php, right?) to use a different directory than /var/www/mollify/[client|server] for the scripts, move them out of the web tree entirely.  I never leave any scripts in the web tree.  My usual structure for sites looks like this:

```

/var/www/public  contains index.php and other publicly-visible stuff
/var/www/include contains all the scripts accessed by index.php

```

So in your case I'd put the mollify directory under /var/www/include, but put the index.php file in /var/www/public or maybe in /var/www/public/mollify.  Then I'd tell index.php to look in /var/www/include/mollify for the client and server directories.

---

### Post by [pl]ice on 2012-12-09
Hi,

Can't do.  Mollify manual said that the main script can be relocated only in the lower part of folders, not upper, so the index in /var/www/public won't find the scripts in /var/www/include.  it can only find it in /var/www/public and deeper in public :(
i might try AjaXplorer  instead :/

---

### Post by SeijiSensei on 2012-12-10
I meant you would need to rewrite at least index.php and perhaps a configuration file to point to a different directory.

If the scripts are merely included in a shell page, usually index.php, there is no technical limitation to having them be located elsewhere.  Usually people who distribute packaged PHP applications take the route of putting everything under the site's DirectoryRoot.  Many people simply rent space from a web host and have no ability to put anything outside the DirectoryRoot.  But if you have full control over the server, there is no reason not to structure the site in a way that makes you feel more secure.

---

