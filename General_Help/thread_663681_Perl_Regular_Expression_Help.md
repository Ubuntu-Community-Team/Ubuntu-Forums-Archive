---
title: "Perl Regular Expression Help?"
date: 2008-01-10
forum: General Help
---

### Post by robulus on 2008-01-10
Hi Folks,
I don't know whether this is the correct forum to post for something like this - so apologies if this shouldn't be here!!

I'm trying to come up with a perl regular expression one-liner that will replace <? on a line with <?php
(<? will be the only string on that line)

my first attempt is this:
perl -pi -e 's/^<\?$/<\?php/g' *.php

which in my head means, if <? is the only string on a line, replace it with <?php

but errr it doesn't work - any pointers?  The perl oneliner looping through the .php files  works - it's just the pattern itself that's at fault.

Running :%s/^<?$/<?php/g within Vim works - so I would have thought the pattern was correct 8-/
thanks!
Rob.

---

### Post by MartynA on 2008-01-10
I just started regex so I had a look at this as a chance to practice. I created a file (regextesting)

<?
<?fgd

and ran:

perl -pi -e 's/^<\?$/<\?php/g' regextesting

to create:

<?php
<?fgd

Which I guess is what you wanted, so it works for me. There must be something else wrong?

PS. using Perl 5.8.8

---

### Post by robulus on 2008-01-17
Hi Martyn - cheers for taking a look at this, and apologies about the delay in replying!

You're right, something odd does seem to be happening:
perl -pi -e 's/^<\?$/<\?php/g' *.php
worked fine on another bunch of practically identical files I had transferred to my local machine, and I'm using the very same version of perl that you are.

No special characters are in the original set - when you type
:set list
under vi it'll show any/all of these that are in the file. (:set nolist clears this view).

In the end I just manually did it - took about 30 mins, but this was a lot shorter than the amount of time I spent trying to debug it 8-/
Rob.

---

