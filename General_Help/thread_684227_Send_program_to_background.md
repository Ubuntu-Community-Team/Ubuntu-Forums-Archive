---
title: "Send program to background"
date: 2008-01-31
forum: General Help
---

### Post by outthere_3 on 2008-01-31
Hi All,

I am having trouble with the background command '&' in my script.

This is the line I am trying to run it on.

gnuplot -persist gnuplot.txt &

This does not seem to send gnuplot to the background.

Can anyone help.

Jeremy

---

### Post by hokiejp on 2008-01-31
I'm not sure exactly what you're trying to do, but the & puts it in the background for me.

If the problem is that you're still seeing the output from gnuplot when you run your script, you can redirect the output somewhere else.  Try:

gnuplot -persist gnuplot.txt 2> /dev/null &

If you wanted to see the output later you could replace '/dev/null/' with 'gp_output.txt' or whatever file you wanted it to wind up in.  You can find more detail under 'REDIRECTION' in the bash man page.

If you want to put commands in your script to send to gnuplot, you can do that with a 'here document', as described here:  [ http://tldp.org/LDP/abs/html/here-docs.html ]("http://tldp.org/LDP/abs/html/here-docs.html").

---

