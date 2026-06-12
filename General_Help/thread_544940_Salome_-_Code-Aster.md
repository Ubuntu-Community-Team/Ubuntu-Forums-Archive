---
title: "Salome - Code-Aster???"
date: 2007-09-06
forum: General Help
---

### Post by Hayesio on 2007-09-06
Hi everyone

I'm an engineer and have been looking for an FEA suite to run on my ubuntu box.  I came across Salome and code aster.  From what i've read Salome is a pre and post processor and Code_aster is the solver.
Is this right? 
 Also, i downloaded and installed salome (binary) and it 
seemed to install alright. I opened the program the first time from the installer shield and it ran ok.  Then i closed it and now can't figure out how to run it again. Any ideas?
Also, now that I've installed salome, do i need to install code-aster aswell, or does salome come with code-aster?. 

Any info on these packages would be greatly appreciated.
Thanks

---

### Post by Fingolfin on 2007-09-26
It is right, Salome is pre- and post processor, and Code Aster is the actual FE solver.
At the moment, they are being developed separately, with the talks going on for some time that the full integration was planned, but it has not materialised yet.
In theory, you can run other solvers with Salome.
If you are having trouble with installing them properly on Ubuntu, there is an alternative way.
PC-Linux based distribution built around Salome and Code Aster by J. Cugnoni. All you have to do is download and burn the ISO file on a DVD, and run it like Knoppix.
[http://lmafsrv1.epfl.ch/jcugnoni/PcLinuxOsAster/](http://lmafsrv1.epfl.ch/jcugnoni/PcLinuxOsAster/)

---

### Post by schristo on 2007-11-19
SALOME and Code Aster are not directly related. SALOME is a platform with the intention to integrate pre and post-processing, as well as coupling between a large number of codes for various engineering and scientific tasks. It has *nothing* to do with FE or with any solver for that matter, you can simply use it as a MED file viewer or as CAD software if you wish to.

This means that SALOME will not come bundled with Code Aster or any other code, you need to install these codes separately. In addition, you need to create modules that interface the code with SALOME. In the case of Code Aster, the nice people at CAELinux have already created it, so you should use their module. Actually, if you want to use SALOME with FE codes, just get a CAELinux DVD and try it out, it has many more FE codes bundled so it should give you a better idea of what you can achieve with it.

As for runnning SALOME, it should have created a salome_appli_3.x.x directory in your home dir, just go in there and run the runAppli script. It prepares the environment and runs SALOME.

---

### Post by nuir on 2007-12-30
For all who are interested in these two great programs, a new official package called [COLOR="Red"]**Salome-Meca**[/COLOR] has been released. This package includes Salome and Code_Aster combined into a single application.

You can find more info directly on the CAElinux site. The great thing about this new release, is that it comes as a standalone pre-compiled package!

Here's a [[COLOR="Sienna"]_link_[/COLOR]]("http://caelinux.com/CMS/index.php?option=com_content&task=view&id=42&Itemid=2") from where you can get more info and download it.

---

