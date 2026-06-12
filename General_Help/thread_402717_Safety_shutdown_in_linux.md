---
title: "Safety shutdown in linux?"
date: 2007-04-06
forum: General Help
---

### Post by mickbuntu on 2007-04-06
Hello,


Question below  you may feel free to skip this or read it too:cry: . I could not resist as went bit soft  on human side of things. Sometimes emotions, just overrule.

.........
My moment of silence before proceed to my question as trying to get back on track. As exactly last week nearly at the time of this post  I lost my favorite pet of 14 1/2 years. She died in the most gruesome way possible  as I was constantly mopping the floor for days when she was bleeding.  She had Cancer, and it spread quicker then we would imagine. It was so painful that our Vet / his staff expressed sympathy in mailing us a letter.  It was heart breaking as the dog loved us very much. Those that have pets know very much that they become part of the family.  She licked me, drank from the children's water bottle Milk. As i tried feeding her when she no longer could eat solids. As metastasis had  likely made its way to her esophagus from her  nipples.   Even in her final 24 hours of her life she still confided in me and my family.  Words can not describe the loose we felt even though she was supposedly by science / laws  a  "dog" "property" to us she was like nearly another human. Although a  bit  slower  form of a human that would be a child forever. Despite that you would  (to  dog  / pet lovers) not believe  the level of intelligence she had.   In pain or not she had  a  "self" and things she knew how to do well. When she was in pain she was  not wanting to go until she met every member in the house. She waited for members to come home greet and fall. Where I made sure the falls would not  hurt her more. As she started falling I would grab with both hands her belly and gently lay her down. It seems she was trying to slow down her death. Her spirit for a short while defeated the process of dying. Which escaped all the laws in the book of death. Last few  hours with us, she made loud "call" I came petted she stopped. I left, she made another call. Which seemed she wanted me to be by her, but it was late in the night. Came back, my mom came  next to her. She stopped calling and felt content.  That is where she proceeded  to dying, she went into a coma and few hours. I would guess she was "brain dead" as  her heart and respiration continued until about 8 AM by 9AM  my mom runs to me as I was getting ready for morning. She says, I think  the dog has passed away. I came back and felt she was still warm.  But no longer breathing, eyes open, tongue to her side  back teeth and mouth open.   Was able to approximate her  passing to be very very recent. As  her stomach  still grumbled  as well and she had a  very very faint  every 2 ? minutes pulse / heart beat. After which that stopped too.:cry: [-( 

end of respect  clause...............


Question does linux operating system have an emergency shutdown system  or should I wait for bios to intersect will it?  That is say noone is around "home" and I am running a server.  God forbid something overheats I want the system to just power off. Rather then say start smoke  <fire> as sometimes fans  wear off. Something needs to signal to the operating system to turn off.

Thanks.

---

### Post by spankymasterc on 2007-04-06
Doesnt your bios detect overheat and automatically shut down? For me i could set up the temp it auto shuts down i have it at 75 C but my system barely ever goes over 50 maybe 45 the most at full load becuase i got a pretty big cpu fan..... so i dont know 

ohh and the safest way to shut down the pc is trough terminal u type

> sudo shutdown -h now

---

### Post by nocturn on 2007-04-06
I haven't tried this, but...

You can have your power button do a suspend when pushed once and a hard power off when pressed 4 seconds.

Now, the suspend is called from a setting file in the acpi package.  You can replace the action on button pressed with shutdown -h now (or sudo shutdown -h if it does not run as root).

---

### Post by mickbuntu on 2007-04-13
Thanks for the replies, I appreciate it very much. I think my bios does it but not on software level.

I set mine to shutdown on  50C  just to be  safe to make sure cpu is aight.

---

