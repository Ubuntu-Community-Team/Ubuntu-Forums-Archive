---
title: "hexadecimal combinbation list file"
date: 2007-08-02
forum: General Help
---

### Post by fdrake on 2007-08-02
hello to all my ubuntu fellows.  i have a request to ask ( for all of them who are able to do this). i need to generate a list of all the possible combination of a set of 12 hexadecimal values. something like this :

  00 00 00 00 00 00 
  00 00 00 00 00 01 
  00 00 00 00 00 02
  00 00 00 00 00 03
           .  .(AND SO ON)   .
  A2 EF 42 1D 00 0C
  A2 EF 42 1D 00 0D
  A2 EF 42 1D 00 0E
           .     .   (AND SO ON)
  FF FF  FF FF FF FD
  FF FF  FF FF FF FE
  FF FF  FF FF FF FF
         
 Now i know that the total number of possible combination is 16^12= 281474976710656 combinations ! that means is going to create a file list of the size of about  3659.2 TB , waayyy to heavy process  for my poor  pc ! that's way i'd like to have a program that gives me all the possible combination between 2 given limits. for example if i type in 
 01 23 45 67 89 AB    and  01 23 45 67 FF 12   then that program would give me the list of all the possible combinations between those two values . i was going to do something like this in perl but i am still a beginner. any help, thought or correction would be immensly appriciated . thank you in advance.

---

### Post by nitro_n2o on 2007-08-02
i think you should post this in the programming forum.. you'll get all sorts of answers ;)

---

### Post by avik on 2007-08-02
Are you sure this is isn't a class assignment or something? ;)

Try posting your idea, and we'll take a look at it.  That way, you can learn a little more by trying it yourself.

---

### Post by stylishpants on 2007-08-02
Here's a ruby solution.


```

ruby -e 'a,n=ARGV; (a.to_i ... n.to_i).each { |i| s="%012X" % i; puts s.gsub(/../,"\\0 ") }' 9 28
00 00 00 00 00 09 
00 00 00 00 00 0A 
00 00 00 00 00 0B 
00 00 00 00 00 0C 
00 00 00 00 00 0D 
00 00 00 00 00 0E 
00 00 00 00 00 0F 
00 00 00 00 00 10 
00 00 00 00 00 11 
00 00 00 00 00 12 
00 00 00 00 00 13 
00 00 00 00 00 14 
00 00 00 00 00 15 
00 00 00 00 00 16 
00 00 00 00 00 17 
00 00 00 00 00 18 
00 00 00 00 00 19 
00 00 00 00 00 1A 
00 00 00 00 00 1B 
```

---

