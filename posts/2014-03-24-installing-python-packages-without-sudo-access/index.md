---
title: How to Use Remote Servers for Deep Learning: Part 1
date: 2014-03-24
author: Eliana
mathjax: on
---

Motivation
------------

I recently became somewhat obsessed with neural nets. But training a convolutional net made normal computer activity tricky. Training two convolutional nets at once would make my laptop freeze up. And forget about training a net with Lin et. al.'s [Network in Network] architecture.

[Network in Network]: http://arxiv.org/abs/1312.4400


Finding More Computing Power
-------------

I don't attend university nor work for a major software company, so I don't easily have computer clusters at my disposal. Luckily, I have friends who attend university!

A friend gave me his login info for his university. Because I would be ssh'ing in a bunch, I edited my <code>.ssh/config</code> file[^1]:

[^1]: stuff in caps is for privacy; replace with actual info

```haskell
Host HOST
User USER
Port 22
HostName HOST.UNIVERSITY.edu
```

and ssh'ed in[^2]:

[^2]: I couldn't use ssh with an authentication key instead of a password due to server configurations, but that is generally recommended.

```bash
$ ssh HOST
```

Python was already installed, but my neural nets code needed [Theano]. Following the instructions for [easy installation]:

[Theano]: http://deeplearning.net/software/theano/
[easy installation]: http://deeplearning.net/software/theano/install_ubuntu.html

```bash
$ sudo apt-get install python-numpy python-scipy python-dev python-pip python-nose g++ libopenblas-dev git
$ [sudo] password for USER:
$ USER is not allowed to run sudo on HOST.  This incident will be reported.
```

Hwrm, right, I don't have sudo access. Sidenote: I'm sure many students messing around with unix have nearly had heart attacks from this message[^3].

[^3]: [relevant xkcd]

[relevant xkcd]:http://xkcd.com/838/



Installing Python Packages without Sudo Access
-----------------------------------------------

First, I needed Theano's dependencies ([NumPy] and [SciPy] -- luckily, the server already had [BLAS]), and a way to install them. For added fun, the server didn't have [pip] or [easy_install].

[NumPy]: http://www.numpy.org/
[SciPy]: http://www.scipy.org/
[BLAS]: http://en.wikipedia.org/wiki/Basic_Linear_Algebra_Subprograms
[pip]: https://pypi.python.org/pypi/pip
[easy_install]: https://pythonhosted.org/setuptools/easy_install.html