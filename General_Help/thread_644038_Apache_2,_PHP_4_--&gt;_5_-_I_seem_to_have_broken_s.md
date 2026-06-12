---
title: "Apache 2, PHP 4 --&gt; 5 - I seem to have broken something."
date: 2007-12-18
forum: General Help
---

### Post by Cordate on 2007-12-18
I have had a web server running with some flavor of Apache2 and PHP 4, and today I was attempting to add the php GD libraries so that this new Joomla site I have put up would be happier. 

Not remembering I didn't have php5, I ran apt-get install php5-gd and this seems to have broken things. 

When I visit any of my locations that use php, my browser asks me if I want to download a php script >.< 

I do have index.php in the DirectoryIndex part of Apache2.conf, and regular html pages are working fine. I suspect it's a matter of pointing something at the php installation somewhere, but I don't know where to look. 

Thanks in advance for any light that can be shed on the matter!

Edit: Still not fixed, but I -can- make a php.info page work and display that information. Help? :)

---

