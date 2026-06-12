---
title: "How can I change the format of a bash script output?"
date: 2018-02-17
forum: General Help
---

### Post by julianment on 2018-02-17
Hey,

I'm trying to change the output to my bash script to a .csv friendly format (separated by commas), specifically IM-Sensors. Currently my output looks like this when I run it. 
[IMG]https://i.imgur.com/QrNNmkZ.png[/IMG]
How can I automatically change the format so I can place this all in the same line and then to put a comma in between?

Thanks for reading!

---

### Post by Claus7 on 2018-02-17
Hello,

just for a clarification, which might help also other users to give you better guidelines:
which is the command you are using in order to have such an output?

I think that you are trying to issue the command: sensors
In order to send the output to a file you can type: sensors > name_of_file_you_want.csv

Now about the comma, awk might do the trick:
sensors | awk -F "," '{print $0 ","}' > test.csv

Is this what you are looking for?

Regards!

Oh! And welcome to the forum!

[Edit: checking your one line question this might be better:
sensors | awk '{printf "%s" ",", $0}' > test.csv ]

---

