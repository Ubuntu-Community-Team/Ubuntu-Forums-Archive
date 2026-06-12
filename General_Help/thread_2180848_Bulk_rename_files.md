---
title: "Bulk rename files"
date: 2013-10-14
forum: General Help
---

### Post by TheOnlyChosenOne on 2013-10-14
I have a script that renames files in bulk. Every file is renamed immediately and sequentially, which means that there is no sleep between the renamings. Sometimes a file will be renamed to a file that existed a nanosecond before the renaming. (eg file1-> file2, file0 -> file1)
Is this a problem (is there a chance that I lose some files) or is this perfectly safe (Ubuntu makes sure nothing corrupt happens)?
The filesystem is ext4.

---

### Post by Vaphell on 2013-10-15
name change is instant so the moment it happens, the old name is up for grabs. That said, depending on the code, the order of operations might be important if there are no safeguards put in place (no, ubuntu has nothing to do with low level stuff in terminal).

care to show the relevant parts of the script?

---

### Post by TheOnlyChosenOne on 2013-10-15
It is a perl script which renames random files to 000.ext 001.ext 002.ext ...
If the filename already exists (-e $newPath), that file will be renamed recursively, so this way nothing gets overwritten.
Is this what you mean by 'safeguards'?
```
for(my $i = 0; $i < $amountOfFiles; $i++){
    if(!$renamed[$i]){
        renameImage($i);
    }
}

sub renameImage{
    my $number = $_[0];
    my $oldName = $oldImageNames[$number];
    my $oldPath = $workingDirectory."/".$oldName;
    my $curExtension = getExtension($oldName);
    my $newName = addZeros($number, $amountOfNumbers).".".lc($curExtension);
    my $newPath = $workingDirectory."/".$newName;
    if($oldPath eq $newPath){
        print "$oldName is already a correct name.\n";
    }
    else{
        if(-e $newPath){
            my $blockingNumber = binarySearch($newName);
            renameImage($blockingNumber);
        }
        print "mv ".$oldPath." ".$newPath."\n";
        system("mv ".convert($oldPath)." ".convert($newPath));
        $renamed[$number] = 1;
        #usleep($waitingTime);
    }
}
```
I think 'binarySearch' is obvious. You can ignore 'convert'.
Just asking if the 'usleep' should be commented out. I've tried it a number of times and nothing gets lost.
But I just want to be 100% sure.

---

### Post by TheOnlyChosenOne on 2013-10-16
Just to have a quick answer.
If I'm doing:
```
 foreach $file ($directory){
    randomly_rename_file($file);
}
```
Will this be okay?

---

### Post by Vaphell on 2013-10-16
not a perl pro but if with every file you check for existence of a file with the target name (yes, something like -e $file is what i meant by safeguards) to see if there is a collision then you should be ok.

Run some tests - generate a bunch of randomly named files, count them, run the script and see if the number of files is the same. If the numbers are not equal then there's a problem.

---

### Post by TheOnlyChosenOne on 2013-10-16
Yes. I do that.
All tests are fine.
PS: Moving (renaming) the files is done with a system command. Thus an actual linux command.

---

### Post by Vaphell on 2013-10-16
yes, it's a linux thing but it's low level and as with most low level cli things it assumes you know what you are doing. Ubuntu or any other distro has nothing to do with it, because distros are simply DEs slapped on top of kernel+command line environment with a selection of programs installed out of the box.

In case of *mv* you can use -i/--interactive to ask for overwrite confirmation or -n/--no-clobber to not overwrite or -b/--backup to autorename colliding files, but you still have to provide these params, if you don't *mv* won't care.

---

