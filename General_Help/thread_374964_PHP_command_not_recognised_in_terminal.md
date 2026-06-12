---
title: "PHP command not recognised in terminal"
date: 2007-03-03
forum: General Help
---

### Post by dery on 2007-03-03
It`s been three days since I run Ubuntu, and I`ve got the hang of it. I`ve single sidedly resolved the monitor resolutoin&refresh rate problem, installed various software, etc. So I understood the principles of Ubuntu. I have Apache2, Subversion, MySQL and PHP5 (version 5.2) installed. The problem is that when I run the command "php" (or "sudo php") an error apears saying that there is no such command/program called php. I know I have it, as I installed it, and even did the "http://localhost/testphp.php", as shown on the [[COLOR="SandyBrown"]UbuntuGuide[/COLOR]]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PHP5"), and it worked.

What do you think?

---

### Post by kidders on 2007-03-03
Hi there,

I'm glad you're enjoying Ubuntu. :-)

There are a few types of PHP installation. You may have opted for the Apache plugin (module), which doesn't include a command line binary. If your primary use for PHP is with web pages, then this was the correct (more secure) choice.

If you wish, you can also install a CLI version (eg **php5-cli**), for use in command line scripting, etc. It would be seperately configurable, using its own php.ini file. Running multiple PHPs on your system at once should be perfectly fine ... they don't even have to be the same versions.

---

### Post by dery on 2007-03-04
Many thanks Kidders :) 

I have googled a little, and now I`ve got php-cli :cool: 

Here is for anyone who might read this in the future, looking for answers to the same problem:

Run the command [COLOR="Blue"][SIZE="2"]sudo apt-get install php5-cli[/SIZE][/COLOR]

---

