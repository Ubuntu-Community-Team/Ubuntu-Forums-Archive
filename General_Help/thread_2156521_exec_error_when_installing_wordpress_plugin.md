---
title: "exec error when installing wordpress plugin?"
date: 2013-06-22
forum: General Help
---

### Post by caleb12134 on 2013-06-22
Whenever I try to install this real estate wordpress plugin called "Real Estate Website Builder" and I click activate it gives me this error. Also the server is mine and is at my house and i am using a zpanel account i created for my moms real estate that is hosted on my server. My server uses linux ubuntu? How do I fix this error? I really appreciate it. 

[COLOR=#333333][FONT=sans-serif]Plugin could not be activated because it triggered a **fatal error**.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times]Warning: exec() has been disabled for security reasons in /var/zpanel/hostdata/christina/public_html/omegarealtorsgroup_tk/wp-content/plugins/placester/third-party/mixpanel/mixpanel.php on line 28[/FONT][/COLOR]

---

### Post by SeijiSensei on 2013-06-22
Are you running this site with PHP's "safe mode" enabled?  If so, you [cannot use exec()]("http://php.net/manual/en/features.safe-mode.functions.php") or any other shell execution command unless the executable resides in the safe_mode_exec_dir and does not include ../ in the path.

That seems to be the only directive that applies here.  Look in /etc/php5/apache2/php.ini to ensure that safe mode is disabled.

---

### Post by mindfulhacker on 2013-06-28
> **SeijiSensei said:**
> Are you running this site with PHP's "safe mode" enabled?  If so, you [cannot use exec()]("http://php.net/manual/en/features.safe-mode.functions.php") or any other shell execution command unless the executable resides in the safe_mode_exec_dir and does not include ../ in the path.

That seems to be the only directive that applies here.  Look in /etc/php5/apache2/php.ini to ensure that safe mode is disabled.

Hey SeijiSensei,

Safe-Mode has been Disabled And exec has been removed from our Disable_functions list. Here is our following configuration:

[http://www.mindfulhacker.tk/php.ini](http://www.mindfulhacker.tk/php.ini)

---

### Post by SeijiSensei on 2013-06-28
What if you just start with a a simple script like this:

```

<?php
exec("echo 'Yes, I can run this!'");
?>

```

Does that fail?

I don't use zpanel or anything similar, so I can't say how that might interfere.

Any "../" constructs in the path name of the script being invoked?

Maybe the problem is that the www-data doesn't have privileges to run whatever is being invoked in exec()? I would think you would get a different error message, but it's worth checking like this:

```

$sudo su
[enter your password]
#su www-data
$/path/to/your/script
$exit
#exit

```

Does it run using this method?

I searched to see if I could find anything about running shell scripts from Wordpress, but didn't get very far.

Have you checked /var/log/apache2/error.log?  Does it help?

---

