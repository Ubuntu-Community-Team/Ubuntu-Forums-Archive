---
title: "computeIntersections in OSG"
date: 2008-06-16
forum: General Help
---

### Post by rajesh.karnik on 2008-06-16
Hello,

I am new to OSG and have recently started to explore the same.

Currently i am using the computeIntersections function of osgProducer::Viewer to pick objects(Nodes/Geodes) from the scene.

I am getting the selected objects in osgUtil::IntersectVisitor::HitList.

But the problem is, when i click on the object (say some cube) i don't get a cube selected. But if i click on the right side of the cube then it gets selected. This is true for all the .osg file  i have tried.

Can any one help me to know this strange behavior of osgProducer::Viewer?

---

### Post by bapoumba on 2008-06-16
Moved to "General Help"
PS/ I googled a bit, but I have no idea what you are asking about..

---

### Post by cyberdork33 on 2008-06-16
> **bapoumba said:**
> Moved to "General Help"
PS/ I googled a bit, but I have no idea what you are asking about..I think he is talking about Open Scene Graph which is a OpenGL toolkit.

---

### Post by rajesh.karnik on 2008-06-18
hello,

I am working on Open Scene Graphics (OSG) which is a wrapper over OpenGL (Open Graphics Library) used to create applications in 3D Domain.

Here, i was trying to develop a pick functionality using a Mouse.

so the expected process is, if i take my mouse pointer on any entity / object of a model, it should get selected and then i will highlight that entity / object.

Currently i am getting the selected object and i am able to highlight the same.

But the problem is i don´t get selection when i take my mouse pointer on the entity/object. But it gets selected when the mouse pointer is on right hand side of the object.

Sounds strange!!!

I think it is some viewers problem.

But no exact idea.

---

