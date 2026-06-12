---
title: "Changing the first number in a filename"
date: 2007-09-24
forum: General Help
---

### Post by delfick on 2007-09-24
Hello, I have a number of files named like

1_1.mp3
1_2.mp3
1_3.mp3
2_1.mp3
2_2.mp3
3_3.mp3
....etc etc

For a flash project I've undertaken.........
(the first number is the number of the section, second number is the number of the page of that section that the music file belongs to)

anyway, sometimes things change and I have to change the names of the files

so say I add a new section between section 1 and 2, then I have to change every music file after that to reflect the new number of their section.

so
2_x -> 3_x
4_x -> 5_x
etc

I was wondering, if I ever had to do that, how I'd be able to tell the terminal:

for the number before the first underscore in all the files;
for a certain range of numbers;
add a particular number to that number in the filename;


??

thnx :D

---

### Post by Maxtorm on 2007-09-24
Assuming the section numbers stay as single digits, you can use something like
```
rename 'y/1-8/2-9/' *_*
```If they start into two digits or more, you'll need to do each move sequentially:
```
rename 's/12/13/' *_*
```As you likely realize, you should do this starting with the higher number and work your way down, otherwise your renames will be overwrite existing files.

---

### Post by delfick on 2007-09-24
> **Maxtorm said:**
> Assuming the section numbers stay as single digits, you can use something like
```
rename 'y/1-8/2-9/' *_*
```If they start into two digits or more, you'll need to do each move sequentially:
```
rename 's/12/13/' *_*
```As you likely realize, you should do this starting with the higher number and work your way down, otherwise your renames will be overwrite existing files.

Problem with the first command is that it changes the number after the underscore as well so 2_3 becomes 3_4.........

also, it doesn't seem to do them from highest to lowest itself complaining that some of them already exist as it's doing it

(and I see why I have to do the two digit ones seperately, 13_2 becomes 24_3)

here is a before and after
```
iambob@iambob-linux:~/Desktop/sound$ ls
1_1.mp3  3_2.mp3   4_11.mp3  4_5.mp3   5_1.mp3  5_7.mp3  6_4.mp3  8_2.mp3
2_1.mp3  3_3.mp3   4_12.mp3  4_6.mp3   5_2.mp3  5_8.mp3  6_5.mp3  8_3.mp3
2_2.mp3  3_4.mp3   4_1.mp3   4_7.mp3   5_3.mp3  5_9.mp3  7_1.mp3  8_4.mp3
2_3.mp3  3_5.mp3   4_2.mp3   4_8.mp3   5_4.mp3  6_1.mp3  7_2.mp3  8_5.mp3
2_4.mp3  3_6.mp3   4_3.mp3   4_9.mp3   5_5.mp3  6_2.mp3  7_3.mp3  
3_1.mp3  4_10.mp3  4_4.mp3   5_10.mp3  5_6.mp3  6_3.mp3  8_1.mp3
iambob@iambob-linux:~/Desktop/sound$ rename 'y/1-8/2-9/' *_*
4_9.mp3 not renamed: 5_9.mp4 already exists
5_9.mp3 not renamed: 6_9.mp4 already exists
iambob@iambob-linux:~/Desktop/sound$ ls
2_2.mp4  4_3.mp4  5_20.mp4  5_5.mp4  6_20.mp4  6_7.mp4  7_5.mp4  9_3.mp4
3_2.mp4  4_4.mp4  5_22.mp4  5_6.mp4  6_2.mp4   6_8.mp4  7_6.mp4  9_4.mp4
3_3.mp4  4_5.mp4  5_23.mp4  5_7.mp4  6_3.mp4   6_9.mp4  8_2.mp4  9_5.mp4
3_4.mp4  4_6.mp4  5_2.mp4   5_8.mp4  6_4.mp4   7_2.mp4  8_3.mp4  9_6.mp4
3_5.mp4  4_7.mp4  5_3.mp4   5_9.mp3  6_5.mp4   7_3.mp4  8_4.mp4  
4_2.mp4  4_9.mp3  5_4.mp4   5_9.mp4  6_6.mp4   7_4.mp4  9_2.mp4

```

thnx for the help anyways :D

---

