---
title: "How to use this git repository to have the software"
date: 2021-05-16
forum: General Help
---

### Post by jean443 on 2021-05-16
Hi,

I want to use this software wich is only on the repository :
[https://github.com/Wikinaut/paperback-cli](https://github.com/Wikinaut/paperback-cli) .

But I don't understand how to build it and install it on my system, so I hope someone can help me.

---

### Post by Impavidus on 2021-05-16
First of all, note that the last update of that project was 4 years ago (apart from an update to the readme file 3 years ago). A perfect program may not need any more updates, but I'd be a bit hesitant to use such software. If I wanted a paper backup of some binary file, I would convert it to ascii in base64 or hexadecimal, then print that text file &#8211; in a really small font.

To use this, you need git to download the source code from the web. You also need gcc to compile it (it's in C), header files and make to tie it all together. It says you don't need any external dependencies, so the headers for the standard libraries should be all you need.```
sudo apt install git gcc libc6-dev make
```
Go to the directory where you want to store the source code (create it first if you need) and clone the repository:```
git clone https://github.com/Wikinaut/paperback-cli.git
```Then follow the instructions in the readme file.

Note that installing software from source code is considered a last resort and not recommended to inexperienced users.

---

### Post by jean443 on 2021-05-16
Thanks, you answered what I had been looking for hours!

I had thought of a system allowing to convert the file into printable characters but I did not know how to do it. If you take a little more of your time to explain the process to me, I you will be really grateful for it!

---

### Post by Impavidus on 2021-05-16
There are undoubtedly libraries to convert binary code to or from hexadecimal or base64 code, but I'd probably just code it myself. It avoids additional dependencies and is a fun exercise.

From binary to hexadecimal: (A) Take one byte of input. If not available, write a final newline and terminate. Pick the highest 4 bits and shift right by 4 (that is, divide by 16, rounding down). If less than 10, add 48 (puts it in ASCII range 0–9), else, add 55 (puts it in ASCII range A–F), write to output. Then pick the lowest 4 bits, perform the same conversion and write to output. If you reached maximum line length, output a newline. Return to (A) for the next byte.

From hexadecimal to binary: (A) Take one byte of input. Terminate if not available. If in range 48–57 (ASCII range 0–9), subtract 48. If in range 65–70 (ASCII range A–F), subtract 55. If in range 97–102 (ASCII range a–f), subtract 87. Else, return to (A). Shift left by 4 (that is, multiply by 16) and store in X. (B) Take one byte of input. Give error and terminate if unavailable. If in range 48–57, subtract 48. If in range 65–70, subtract 55. If in range 97–102, subtract 87. Else, return to (B). Add to X and write the sum to output. Return to (A).

Base64 is a bit more complex and left as an exercise for you. The advantage of base64 is that it only increases filesize by a factor 4/3, where hexadecimal increases filesize by a factor 2.

---

### Post by jean443 on 2021-05-17
Thanks!!!!

---

