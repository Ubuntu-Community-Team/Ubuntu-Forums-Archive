---
title: "synaptic pkg manager question.."
date: 2005-05-22
forum: General Help
---

### Post by kimes on 2005-05-22
I'd been using aptitute in my debian environment.. for a while for my package managing..

because it has this feature..
> 
aptitude tracks automatically installed packages

   Stop worrying about pruning unused libraries and support packages from
   your system. If you use aptitude to install everything, it will keep
   track of what packages are pulled in by dependencies alone, and remove
   those packages when they are no longer needed.


but in ubuntu actually i can use aptitude.. but i'd prefer use synaptic package manager..

Is there that kind of feature in 'synaptic'?
(I couldn't find it)

---

### Post by jobezone on 2005-05-22
You can install deborphan and use it in the comand line (run 'man deborphan' and look at /usr/share/doc/deborphan/README.gz for the documentation of it), or you can use Synaptic to help you a bit. 
1 - In Synaptic, open the Configurations->Filters
2 - Add a new filter clicking New, and change the name to Orphaned packages
3 - In the pane "State" only check "orphan"
4 - Click OK

5 - Now you have a filter which will show you packages which deborphan finds that "have no packages depending on them. The default operation is to search only within the libs  and  oldlibs  sections to hunt down unused libraries."(from deborphan's man page).

I don't if it's possible to configure how deborphan is used by Synaptic.
And the possibilites for filtering in synaptic seem amazing, and I have yet to examine them all (there are three panes you can use when filtering packages: State, Section and Properties(of individual packages, like their name, their author, and many others).

---

### Post by kimes on 2005-05-22
[QUOTE=jobezone]You can install deborphan and use it in the comand line (run 'man deborphan' and look at /usr/share/doc/deborphan/README.gz for the documentation of it), or you can use Synaptic to help you a bit. 
1 - In Synaptic, open the Configurations->Filters
2 - Add a new filter clicking New, and change the name to Orphaned packages
3 - In the pane "State" only check "orphan"
4 - Click OK

5 - Now you have a filter which will show you packages which deborphan finds that "have no packages depending on them. The default operation is to search only within the libs  and  oldlibs  sections to hunt down unused libraries."(from deborphan's man page).

I don't if it's possible to configure how deborphan is used by Synaptic.
And the possibilites for filtering in synaptic seem amazing, and I have yet to examine them all (there are three panes you can use when filtering packages: State, Section and Properties(of individual packages, like their name, their author, and many others).[/QUOTE]
 Thanks for your answer.. 

After I tested your suggestion.. I realized that It's not what i wanted..

Let me say one my case..

I installed package 'a' which has dependency with 'b' and 'c'
That's why 'b' and 'c' has been installed together in synaptic..

And I uninstalled 'a'.. 
in aptitude's case.. when i uninstall 'a', it automatically uninstalled 'b' and 'c' together.. since it keeps track of them..

But in synaptics' case.. especially your suggestion..
It doesn't catch 'b' and 'c' in filter stuff..

is there other way or other filtering method?

Thanks.. in advance..

---

### Post by tread on 2005-05-22
No, as far as I know synaptic lacks that ability. I really wish it had that though .. aptitude isn't that intuitive to use.

---

