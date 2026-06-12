---
title: "Copy from ext4 to fat32 and special chars"
date: 2021-03-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2021-03-13
Before i reinvent the wheel i wanted to ask if anyone knows if there is a good way to sync a dir with another where there are some chars that are not supported on fat like ":", "\", "*", etc. as well as the potential of 2 files of the same name but in different casing which ext4 supports bot not fat32 and following sym links, i can assume any file in the destination is the same or older

Note: what i am doing is copying my ~/Music folder to a micro sd card, but the silly phone (it is old, android 6.0.1) does not appear to let me use ext2, ext3, or ext4 on the card, so I seem stuck using fat32

---

### Post by TheFu on 2021-03-14
Different file systems have different character support. Not much we can do about it. tar can be used to move files around, retaining the Unix names, but that isn't convenient for access on android.
[https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits) shows the differences.

Any f2fs support?  I have an old device. Tested it. It didn't work. Maybe it will on yours?
Does exFAT work? The table isn't clear on character limits for exfat.

---

### Post by HermanAB on 2021-03-14
Can you use FTP or SFTP to copy the files over the network to a Linux machine?

---

### Post by TheFu on 2021-03-14
HermanAB's post got me thinking .... 

That begs the question, what does FAT have to do with transferring files?

The internal storage for Android uses a native Linux file system, so we know that support is possible.  Just be certain to use an "endurance" microSD, like Samsung sells to deal with write counts. I know a 64G one is about $10 during periodic sales.

Many versions of Android support using a native Linux file system on external storage too, provided that is selected during initial device configuration.  So, if you rsync the files over to Android and store them on internal storage, then any valid Linux name will be fine.

I just checked and my Android 6 phone won't let me format the external microSD to ext2/3/4 now, because I've already created multiple userids. I wonder if I purge those extra users, then would I be able to format the external SD to a native Linux file system?  Something to try.
It appears that Android does support ext3/4 natively. Unfortunately, those are all journaled file systems which means they are harder on SD flash storage. Approx. 2x the writes from non-journalled f2fs or exFAT.

Have you tried formatting the SD card to ext3 and inserting it?  I haven't myself, but if f2fs and exFAT don't work well enough (or at all), ext3 should work.

---

### Post by pqwoerituytrueiwoq on 2021-03-14
every time i have tried exfat for ext2/3/4 it either does not show up or says corrupt
I made a php copy script, note it does not handle removed/renamed files in the source
note lines 37/52/69 have hard coded file paths if anyone needs this
```
<?php
function fatSafe($path){
    $bad = ['*',':','\\','"','<','>','|','?'];
    $good = ['&#65290;','&#720;','&#12341;','&#12443;','&#12296;','&#12297;','&#448;','&#65311;'];
    return str_replace($bad,$good,$path);
}
function compareFiles($file_a, $file_b){
    //https://stackoverflow.com/questions/18849927/verifying-that-two-files-are-identical-using-pure-php
    if(filesize($file_a) == filesize($file_b)){
        $fp_a = fopen($file_a, 'rb');
        $fp_b = fopen($file_b, 'rb');
        while (!feof($fp_a) && ($b = fread($fp_a, 4096)) !== false){
            $b_b = fread($fp_b, 4096);
            if($b !== $b_b){
                fclose($fp_a);
                fclose($fp_b);
                return false;
            }
        }
        fclose($fp_a);
        fclose($fp_b);
        return true;
    }
    return false;
}
function tree($dir,$depth){
    $scan=scandir($dir);
    foreach($scan as $f){
        if($f=="."||$f==".."){
            continue;
        }
        if(is_dir("$dir/$f")){
            if($depth<10){// Max folder depth, this is to prevent a infinite loop
                $inDir="$dir/$f";
                $outDir=substr($inDir,11);
                $outDir=fatSafe($outDir);
                $outDir="/media/chad/C2DD-12FF/$outDir";
                if(!is_dir($outDir)){
                    echo "mkdir: $outDir\n";
                    mkdir($outDir);
                }
                tree("$dir/$f",$depth+1);
            }
            else{
                echo "Error: $dir/$f is too deep; Infinite loop prevention";
            }
        }
        else{
            $inFile="$dir/$f";
            $outFile=substr($inFile,11);
            $outFile=fatSafe($outFile);
            $outFile="/media/chad/C2DD-12FF/$outFile";
            if(file_exists($outFile)){
                if(!compareFiles($inFile,$outFile)){
                    echo "update: $inFile --> $outFile\n";
                    copy($inFile,$outFile);
                }
                else{
                    echo "same: $inFile == $outFile\n";
                }
            }
            else{
                echo "copy: $inFile --> $outFile\n";
                copy($inFile,$outFile);
            }
        }
    }
}
tree('/home/chad/Music',0);
?>

```

---

### Post by TheFu on 2021-03-14
Don't use fat32.

Why not use rsync for this? I'm confused.

---

### Post by pqwoerituytrueiwoq on 2021-03-14
> **TheFu said:**
> Don't use fat32.

Why not use rsync for this? I'm confused.
fat32 seems to be the only thing the phone will let me use on the sd card
fat32 does not support come chars in file names like :, ?, and *

---

