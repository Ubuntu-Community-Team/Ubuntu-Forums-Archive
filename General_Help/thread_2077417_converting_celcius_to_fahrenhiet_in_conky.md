---
title: "converting celcius to fahrenhiet in conky"
date: 2012-10-28
forum: General Help
---

### Post by dolmance41 on 2012-10-28
I struggled with this for weeks...
here is the code that works GREAT!!!
${font Vibrocentric:style=bold:size=12}${color magenta}CPU Temperature: ${color red}${execi 1200 echo $(($(cat /sys/bus/pci/drivers/k10temp/0000:00:18.3/temp1_input) / 1000 * 9 / 5 + 32)) F}

---

### Post by drmrgd on 2012-10-28
Looks good.  But, I thought that you could pre-define the temperature units used in the header of Conky (search the link below for 'temperature'):

[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

It's been a while since I had any temp specific items in my Conky, but I sort of remember it being easier than doing a math conversion on the fly.  If I'm wrong, though, that's definitely a useful way to do it :)

---

