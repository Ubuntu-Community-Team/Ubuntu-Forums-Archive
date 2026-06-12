---
title: "can this be done?"
date: 2008-03-05
forum: General Help
---

### Post by jon9314 on 2008-03-05
hi i have a file that i need to make every block of 2048 bytes start with ( 00 00 01 BA) in hex.
is there some command i can use  to check the file and automatically change it if needed? i am currently going manualy and the file is 1.4G so it is going to take forever. i know if linux can't do it it probably can't be done. thanks in advance.

---

### Post by ph1 on 2008-03-05
I have little skills as far as coding goes, but you might want to look into regular expressions, as they were once recommended to me for a similar purpose.

---

### Post by SpaceTeddy on 2008-03-06
ok... i have never done something like this before, but i think it can be done with just a few lines of perl (by the looks of it). I looked for perl because regex was mentioned before, but then it occured to me that regex will most likely not be of any help in a binary file.

so, here is my search result.
first, how to handle binary files in perl [http://www.cs.cf.ac.uk/Dave/PERL/node73.html]("http://www.cs.cf.ac.uk/Dave/PERL/node73.html")
what you'd need to do is read the file through in 2048 byte blocks, then change the start of array and write it back to another file. Should all be pretty simple, really... 

i have no time to write the thing myself - but hey, it's a challenge :)

---

### Post by jon9314 on 2008-03-06
i tried to read that page and it was as good as a foreign language to me. thanks for tring

---

### Post by SpaceTeddy on 2008-03-06
the things this forum makes me do :)

here is the perl script to run
```
#!/usr/bin/perl -w

$source = "< in.file";
$dest = "> out.file";
$blocksize = 2048;

@replace_seq = (00,00,01,186); #same as 00 00 01 BA in hex (it's just decimal)

$buffer = "";
open(SRC, $source);
open(DST, $dest);
binmode(SRC); 
binmode(DST);

$i = 0;
while (read(SRC, $buffer, $blocksize, 0)){
  @array = split(//, $buffer);
  
  if ($#array >= $#replace_seq) {
    for ($j = 0; $j < $#replace_seq +1 ; $j++) {
      $array[$j] = chr($replace_seq[$j]);       	
    }
  }
  
  print DST @array;  
 
  if ($i % 1000 == 0) {
    $tmp = $i * $blocksize;
    print "$tmp bytes done\n";
  }
  $i++;
}

close(SRC);
close(DST);
```

edit the three values at the start (DO NOT REMOTE THE < or >, they are important. just change the filenames.

this script will read the infile, and replace the start of each block (a block is defined by blocksize) with the sequence in replace_seq (these are bytes, but they have to be written in decimal, not hex)

at the moment it is set to what you wanted it to do (i think). don't know how long it runs, since this is about the slowest way to copy a file ever... but it is definetly faster than you happily typing away :)

How to run:
copy the script to an empty file, edit the filenames and save it (filename does not matter)
open a console and go into the dir where the file is saved
run ```
chmod +x %FILENAME%
```
where %FILENAME% is the name of the file the script is saved in
start the script by writing```
./%FILENAME%
```

it should give you it's status every 2 Mbyte
you can break and check the result by doing a ctrl+c in the console...

hope it works  (it did for me)

---

### Post by jon9314 on 2008-03-06
you are awesome

---

### Post by SpaceTeddy on 2008-03-07
only one question from my side remais... did it work ?

---

### Post by jon9314 on 2008-03-19
yes it worked.

---

