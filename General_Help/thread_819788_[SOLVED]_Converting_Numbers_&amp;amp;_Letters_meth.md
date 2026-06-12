---
title: "[SOLVED] Converting Numbers &amp;amp; Letters method/program required"
date: 2008-06-05
forum: General Help
---

### Post by Rytron on 2008-06-05
Hi,
Is there a command line or program to download that will convert numbers to letters and letters into numbers quickly(using numbers and letters that correspond to each other in the alphabet)?

Example[convert numbers to letters]:
642 would become FDB

Example[convert letters into numbers]:
cat would be 3120 (that is 3 for c, 1 for a, 20 for t)

---

### Post by HalPomeranz on 2008-06-06
Numbers to letters can be ambiguous: if you give me '3126' is that 'CABF' or 'CAZ'?  So I'm going to assume you're going to give me whitespace separated strings (e.g. '3 1 26') to remove any ambiguity:

```

$ **perl -e 'print join("", map { chr($_ + 64) } @ARGV), "\n"' 3 1 26**
CAZ

```

Letters to numbers has no ambiguity, but I'm going to massage the input a little to remove all non-letter characters first:

```

$ [B]perl -e '$str = join("", @ARGV);
           $str =~ s/[^A-Za-z]//g;
           $str =~ tr/a-z/A-Z/;
           print join(" ", map { ord($_) - 64 } split(//, $str)), "\n";' CAZ[/B]
3 1 26

```

Go Perl!

---

### Post by Rytron on 2008-06-07
> **HalPomeranz said:**
> Numbers to letters can be ambiguous: if you give me '3126' is that 'CABF' or 'CAZ'?  So I'm going to assume you're going to give me whitespace separated strings (e.g. '3 1 26') to remove any ambiguity:

```

$ **perl -e 'print join("", map { chr($_ + 64) } @ARGV), "\n"' 3 1 26**
CAZ

```

Letters to numbers has no ambiguity, but I'm going to massage the input a little to remove all non-letter characters first:

```

$ [B]perl -e '$str = join("", @ARGV);
           $str =~ s/[^A-Za-z]//g;
           $str =~ tr/a-z/A-Z/;
           print join(" ", map { ord($_) - 64 } split(//, $str)), "\n";' CAZ[/B]
3 1 26

```

Go Perl!

Hi HalPomeranz,
I tried your code. Its amazing. Your a genius. Cheers.

:popcorn:

---

