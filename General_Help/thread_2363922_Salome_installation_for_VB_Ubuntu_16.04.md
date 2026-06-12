---
title: "Salome installation for VB Ubuntu 16.04"
date: 2017-06-16
forum: General Help
---

### Post by leosilvero9 on 2017-06-16
Hi all,

I am a newbie user of Ubuntu which I installed to use OpenFOAM. I read that Salome is a good tool for meshing geometries and actually see the generated mesh. 
I had no problem running OpenFOAM but it is difficult for me to install Salome 8.2.0-UB 16.04. After unzipping all the files from the tar.gz file I ended up with a binaries folder, a sources folder, an env_launch.sh file, a python file named salome, a Readme file and some release notes. I donot have a clue how to proceed installing Salome. Based on the Readme file:
This package includes an installation of the application SALOME-8.2.0.

 To run it, launch the following command :
> $ROOT/salome

But this doesn't work when I replace the ROOT directory with the directory of the salome file. 

Could someone have the patience to guide me through the procedure and actually explain to me the purpose of all these folders and files. I am getting very frustrated and at the same time interested and excited using Ubuntu. Hopefully one of the more experienced people here could help me achieve what I am trying to do. 

Thank you,
Leo

---

### Post by leosilvero9 on 2017-06-16
ok I think I got it to run. It was literally just typing at the terminal: python salome
Still if someone can help me understand the other files in my folder would be appreciated. 
Thanks

---

### Post by cydone on 2018-05-22
[LEFT].
OpenFOAM= CFD software ( Computational Fluid Dynamics )
A link towards a YouTube video for the installation of OpenFOAM
[https://www.youtube.com/watch?v=x6BWTEcuh38]("https://www.youtube.com/watch?v=x6BWTEcuh38videoname") 
video name = OpenFOAM 4.0 Computing and Programming_ Installing OpenFOAM4.0 on Ubuntu.mp4
author= CFD Direct #OpenFOAM

I have tested the software in May, 2018.
However instead of installing OpenFOAM 4.0, I have installed OpenFOAM 5.0
It works perfectly

NB1: On youtube, you will find other videos ( tutorial ) to perform CFDcalculations with OpenFOAM.

NB2: OpenFOAM = processor                  
         ParaView/ ParaFOAM ( Integrated into  OpenFOAM ) = post-processeur to see the results         
       
       To mesh a CAD3D-model, you need another software (pre-processor). I use Salome Meca (see below to install it )


[/LEFT]

---

