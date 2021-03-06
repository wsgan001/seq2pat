.. _installation:

Installation
============

.. admonition:: Installation Steps

	The installation consists of two main steps:

	1. Build the backend
	2. Install the library

.. _requirements:

Requirements
------------

* The library requires ``Python 3.6+``, the ``Cython`` package,  and a ``C++`` compiler (gcc, clang or another). See `requirements.txt`_  for dependencies.

* Make sure to use the same Python version to run Seq2Pat and to run the ``setup.py`` script.

* Make sure that the C++ compiler used in your Python installation is the same or compatible with the C++ compiler that you use to build the Cython artifacts. You can see the underlying C++ compiler of your Python installation using ``python -i``.

* On Windows, you can install `MS Visual Studio Build Tools`_ for the ``C++`` compiler.

* On Mac, you can install `Command Line Tools`_ for the ``Clang`` compiler.


1. Build the Backend
--------------------

You can install the required backend artifacts from the source code using ``Cython`` via the ``/sequential/backend/setup.py`` script.

.. code-block:: python

	pip install cython # if cython is not installed
	cd seq2pat/sequential/backend
	python setup.py build_ext --inplace

This command will create the required backend artifacts in the ``/sequential/backend/build`` folder.

2. Install  the Library
-----------------------

Now you can install the library on your platform from a wheel package.

.. code-block:: python

	cd seq2pat
	pip install setuptools wheel # if wheel is not installed
	python setup.py bdist_wheel
	pip install dist/seq2pat-X.X.X-py3-none-any.whl

.. important:: Don't forget to replace ``X.X.X`` with the current version number.

Test Your Setup
---------------

Successful compilation creates ``Cython`` artifacts as seen in the directory structure below.

To confirm that the installation was successful, run the tests included in the project.

All tests should pass.

.. code-block:: python

	cd seq2pat
	python -m unittest discover tests

You can now also import Seq2Pat in a Python shell or notebook.

.. code-block:: python

	from sequential.seq2pat import Seq2Pat, Attribute

For examples of how to use the library, refer to :ref:`Usage Examples<examples>`.

Upgrading the Library
---------------------

To upgrade to the latest version of the library, run ``git pull origin master`` in the repo folder,
and then run ``pip install --upgrade --no-cache-dir dist/seq2pat-X.X.X-py3-none-any.whl``.

.. _MS Visual Studio Build Tools: https://visualstudio.microsoft.com/downloads/
.. _Command Line Tools: https://developer.apple.com/
.. _requirements.txt: https://github.com/fidelity/seq2pat/blob/master/requirements.txt
