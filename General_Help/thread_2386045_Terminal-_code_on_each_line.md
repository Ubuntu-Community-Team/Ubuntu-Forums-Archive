---
title: "Terminal- code on each line"
date: 2018-02-28
forum: General Help
---

### Post by PDA1 on 2018-02-28
Using Terminal, I'd like to place specific lines of commands on separate lines but they must all be carried out once enter is pressed.  Here's an example of how I do it now using;

   User$ pdftk A=file1.pdf  B=file2.pdf C=file3.pdf **cat** A1  C  B6-end output FinalFile.pdf

That's fine but it would be nicer if I could edit the command line like a paragraph using a word processor, paste it into Terminal and then press enter.  Like this;

   

User$ pdftk  
A=file1.pdf   
 B=file2.pdf  
 C=file3.pdf  
 cat 
A1   
C   
B6-end  
 output FinalFile.pdf

Any ideas?

Thanks

---

### Post by HermanAB on 2018-02-28
The backslash character can be used to \
continue \
lines; and the colon; can be used to \
concatenate; commands.

---

### Post by holiday on 2018-02-28
I'm not sure what you're trying to do, but if you want the commands to run concurrently then one solution is to background each one before calling the next. Consider this example. The script identifies itself then sleeps, then prints its exit. You can see they run concurrently. 

# test.sh
#!/bin/bash
printf "This is %s" $1 
sleep 10
printf "That was %s" $1 


$ for t in a b c;do ( ./test.sh $t & );done;

This may not be what you're looking for.

---

### Post by PDA1 on 2018-02-28
Herman,

Thanks for the effort but it doesn't work in when applied to my situation.  Like I said above, I want to be able to easily edit the entire code on separate lines (for my own ease of use) using my word processor and then paste it all into terminal and have it all sequentially carried out.  I want terminal to recognize the stuff I created in the word processor as one entire line.  

Does that help explain it?

Thanks

---

### Post by PDA1 on 2018-02-28
Boy am I "umb-day"

Here it is;

   User$ pdftk \  
A=file1.pdf \
 B=file2.pdf \  
 C=file3.pdf \  
 cat A1 \   
 C \   
 B6-end \
output FinalFile.pdf

'Works perfectly.  Thanks, all.

---

