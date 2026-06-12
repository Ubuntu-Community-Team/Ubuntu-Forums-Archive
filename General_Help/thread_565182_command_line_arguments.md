---
title: "command line arguments"
date: 2007-10-01
forum: General Help
---

### Post by dlieberman on 2007-10-01
When I have the line
   pcapletinst = Pcaplet.new('-s 1500')
in my program, the program runs well without command line arguments, but when run with any command line arguments, the following error message appears:

Exception `Pcap::PcapError' at /usr/local/lib/site_ruby/1.8/pcaplet.rb:56 - setfilter: syntax error
setfilter: syntax error

I would very much appreciate explanation of the cause of the error message.

David

---

### Post by cmnorton on 2007-10-02
What kind of program is it, bash shell script or something else?

I believe you want the environment variable created

pcapletinst=Pcaplet.new('-s 1500')

but we'd still need to see the line where the failure is happening.

---

### Post by dlieberman on 2007-10-03
CMMorton

     Thanks for responding to my post.  It was too vague.  Below is the Ruby test program I am using:

-------------------------------------------
#  ~/progs/cmdargs.rb

  require 'pcap'
  require 'pcaplet'
  require 'optparse'

#  pcapletinst = Pcaplet.new('-s 1500')

  print "\n Start\n\n"
  print "ARGV.size = ", ARGV.size.to_s, "\n"
  print "\nEnd\n\n"
----------------------------------------------

     When the line 'pcapletinst = Pcaplet.new('-s 1500')' is commented out, as above, the program runs correctly, printing the number of command line arguments.  But when the line is uncommented, the program runs correctly only for zero command line arguments. As soon as even one argument is present, the program doesn't run.  Instead I get the message:

Exception `Pcap::PcapError' at /usr/local/lib/site_ruby/1.8/pcaplet.rb:56 - setfilter: syntax error
setfilter: syntax error
-
     It may be significant that even though I have the line  "require 'optparse'", I always get the notification:

Warning:/usr/local/lib/site_ruby/1.8/pcaplet.rb:2: getopts is deprecated after Ruby 1.8.1; use optparse instead

David

---

