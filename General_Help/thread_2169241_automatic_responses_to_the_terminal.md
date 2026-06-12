---
title: "automatic responses to the terminal"
date: 2013-08-21
forum: General Help
---

### Post by iacoposk8 on 2013-08-21
Hello to all! I have to save a lot of video and I'm using the following command within an "each"
avidemux asks me two questions to which I always want to respond you respectively and then not.
how can I indicate my preferences so that the script can operate continuously without my intervention?
thanks :)
```
avidemux2_cli --load 0.MPG --audio-codec copy --video-codec x264 --video-conf 2pass=200 --output-format MP4 --save compress/0.MPG
```

---

### Post by Vaphell on 2013-08-21
looks like a straightforward job for *expect*

---

### Post by iacoposk8 on 2013-08-21
I'm sorry, but I did not understand how I can fix? (my english is bad)

---

### Post by Vaphell on 2013-08-21
[http://www.thegeekstuff.com/2010/10/expect-examples/](http://www.thegeekstuff.com/2010/10/expect-examples/)

---

### Post by iacoposk8 on 2013-08-22
I wrote this but it should be ... it is probably something wrong ... how to fix him?
```
set timeout 10
expect "Yes or No (Y/y or N/n) :"
send "y"
avidemux2_cli --load 00.MPG --audio-codec copy --video-codec x264 --video-conf 2pass=200 --output-format MP4 --save compress/00.MPG
```

---

### Post by Vaphell on 2013-08-22
and what does your main loop look like?

example: expect_test.sh
```
#!/bin/bash

read -p "Question #$1? Yes/No: " answer
echo "Answer: $answer"
```

this loop with inlined expect script
```
for i in {1..5}
do
  expect -c "set timeout 1;
             spawn ./expect_test.sh $i
             expect 'Question'
             send \"Yes\r\"
             interact;"
done
```
yields this
```
spawn ./expect_test.sh 1
Question #1? Yes/No: Yes
Answer: Yes
spawn ./expect_test.sh 2
Question #2? Yes/No: Yes
Answer: Yes
spawn ./expect_test.sh 3
Question #3? Yes/No: Yes
Answer: Yes
spawn ./expect_test.sh 4
Question #4? Yes/No: Yes
Answer: Yes
spawn ./expect_test.sh 5
Question #5? Yes/No: Yes
Answer: Yes
```

---

### Post by iacoposk8 on 2013-08-22
I'm doing the tests, and I commented on now for the cycle "each"
I wrote this:
```
expect -c "set timeout 1;
             spawn avidemux2_cli --load 00.MPG --audio-codec copy --video-codec x264 --video-conf 2pass=200 --output-format MP4 --save compress/00.MPG
             expect 'Yes or No (Y/y or N/n) :'
             send \"Yes\r\"
             interact;"
```
but it tells me:
expect: command not found

---

### Post by steeldriver on 2013-08-22
You need to install the expect package, it's not part of the standard desktop or server

---

### Post by iacoposk8 on 2013-08-23
now it works! thanks :)
last question, if I put the timeout to 10, 100, 1000, 10000, I see that the output of avidemux is always truncated prematurely, putting a number as high as 999999999 instead works ... how come? to display questions pass less than 5 seconds ...
```
expect -c "set timeout 999999999;
        spawn avidemux2_cli --load ${f} --audio-codec copy --video-codec x264 --video-conf 2pass=200 --output-format MP4 --save compress/${f}
        expect 'Yes or No (Y/y or N/n) :'
        send \"Yes\r\"
        send \"No\r\"
        interact;"
```

---

