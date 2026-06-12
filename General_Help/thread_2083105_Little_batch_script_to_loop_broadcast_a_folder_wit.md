---
title: "Little batch script to loop broadcast a folder with ffmpeg"
date: 2012-11-11
forum: General Help
---

### Post by undercash on 2012-11-11
hello,

currently i m using this little script to play a whole folder with ffmpeg. but I d like the script to restart after he completed the play of all the files. How can I do that?


```

for file in *
do
ffmpeg -re -i "$file" (options..) rtmp://live.justin.tv/app/xxxx
sleep 12
done
```

thanks

---

### Post by sisco311 on 2012-11-11
Put the for loop in an infinite while loop:
```
while :
do
    for file in *
    do
        ...
    done
done
```

---

### Post by undercash on 2012-11-11
what to say? thank you!

works exactly as I need.. infinite loop back.. thanks again

---

### Post by sisco311 on 2012-11-11
You are welcome!

Please don't forget  to mark this thread as solved.

---

### Post by undercash on 2012-11-11
will do!

---

