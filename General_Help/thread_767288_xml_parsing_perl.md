---
title: "xml parsing perl"
date: 2008-04-25
forum: General Help
---

### Post by evaristegalois on 2008-04-25
I am trying to get XML::Parser working on perl. The following program
prints out the parsed contents of the xml file on the screen, but I
want to capture them in a file. 

use XML::Parser;
open(input,"<./test.xml");
@input=<input>;
close(input);
$xmlcode=$input[0];
$p1 = new XML::Parser(Style => 'Debug');
$p1->parse($xmlcode);

I called this program test.xml. It's frustrating to see exactly what
you're trying to do flash by on the screen! But STDOUT doesn't capture
it, 

perl test.pl > test.data

won't do anything. Neither will 'open(STDOUT,">./test.data");'

Any suggestions?

---

### Post by Archimedes0212 on 2009-03-16
are you looking for something like this?
[http://articles.techrepublic.com.com/5100-10878_11-5363190.html](http://articles.techrepublic.com.com/5100-10878_11-5363190.html)

---

