---
title: "tar is retarded"
date: 2007-11-19
forum: General Help
---

### Post by Jasper84 on 2007-11-19
I am trying to get tar to append files, according to 'tar --help', -A appends a **tar** and -r appends a file. The latter is not working; it is just printing it all to the screen. I am pretty annoyed :(. (Of course i tried --append too)

So i did this: "tar c-cp1.tar -r dens0.hr-arr" and only got my file printed. I dont see what i could be doing wrong. (it would suck if it was a bug) 

What i was doing was making a loop to add these files, it seems to work with echo. it would be a solution if i could use its output as bash code too. (but i dunno how)
```

while [ $i -lt 9 ]; do
  echo tar c-cp1.tar -r dens$i.hr-arr -r hole$i.hr-arr -r ages$i.hr-arr -r react$i.hr-arr;
  let i=i+1;
done
```
Also tar obviously has an idiotic interface where "tar -cf *" overwrites the first file it sees.

PS sorry for negative tone.

---

### Post by mali2297 on 2007-11-19
> 
So i did this: "tar c-cp1.tar -r dens0.hr-arr" and only got my file printed. I dont see what i could be doing wrong. (it would suck if it was a bug)

tar doesn't understand, you have to speak clearer. :-)

Let me help you with the translation. I suppose that you want to append the file *dens0.hr-arr* to the archive *c-cp1.tar*.  Then type
```

tar -rvf c-cp1.tar dens0.hr-arr

```
If you want to add several files...
```

tar -rvf c-cp1.tar dens0.hr-arr dens1.hr-arr dens2.hr-arr

```
etc.

> 
while [ $i -lt 9 ]; do
  echo tar c-cp1.tar -r dens$i.hr-arr -r hole$i.hr-arr -r ages$i.hr-arr -r react$i.hr-arr;
  let i=i+1;
done

This will give the output
```

tar c-cp1.tar -r dens0.hr-arr -r hole0.hr-arr -r ages0.hr-arr -r react0.hr-arr
tar c-cp1.tar -r dens1.hr-arr -r hole1.hr-arr -r ages1.hr-arr -r react1.hr-arr
tar c-cp1.tar -r dens2.hr-arr -r hole2.hr-arr -r ages2.hr-arr -r react2.hr-arr
tar c-cp1.tar -r dens3.hr-arr -r hole3.hr-arr -r ages3.hr-arr -r react3.hr-arr
tar c-cp1.tar -r dens4.hr-arr -r hole4.hr-arr -r ages4.hr-arr -r react4.hr-arr
tar c-cp1.tar -r dens5.hr-arr -r hole5.hr-arr -r ages5.hr-arr -r react5.hr-arr
tar c-cp1.tar -r dens6.hr-arr -r hole6.hr-arr -r ages6.hr-arr -r react6.hr-arr
tar c-cp1.tar -r dens7.hr-arr -r hole7.hr-arr -r ages7.hr-arr -r react7.hr-arr
tar c-cp1.tar -r dens8.hr-arr -r hole8.hr-arr -r ages8.hr-arr -r react8.hr-arr

```
The command echo won't execute the above lines, just print them.

---

### Post by Jasper84 on 2007-11-19
Thanks for your reply.  Sorry for my rather stupid post, i should have read the docs better. The --help says: " -r, --append  append files to the end of an archive" but that isnt true, as you have to add -rf as well ( so it works like this: -r -f <=> -rf ? and -r -v -f <=> -rvf ?)

BTW i knew about the echo doing that.

---

