---
title: "Error installing XML::Twig"
date: 2007-04-28
forum: General Help
---

### Post by Luc1fer on 2007-04-28
Hi

I'm trying to install xmltv to use MythTV and I'm following this guide (the manual install)
[http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.2](http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.2)

But when i try to install XML::Twig i get the following error
> t/test_with_lwp.....................ok 1/13                                  

### warning is normal here ###

file:test_with_lwp_no_file.xml File `test_with_lwp_no_file.xml' does not exist at t/test_with_lwp.t line 50
t/test_with_lwp.....................NOK 5no file, error message: expected to match /^\s*no element found/, got 'Ran out of memory for input buffer at /usr/lib/perl5/XML/Parser/Expat.pm line 469.
'
t/test_with_lwp.....................FAILED test 5                            
        Failed 1/13 tests, 92.31% okay


I have installed all different modules it complained about and that is the only error left and it's a bit annoying because i haven't found any solution on the web?

Any ideas?

// Andreas

---

### Post by Gil_Gamesh on 2007-07-25
I have this problem too. Did you ever find a solution?

---

### Post by Luc1fer on 2007-07-26
No unfortunately not.

---

