*************************************************************
Extracellular Electrophysiology Acquisition Course Materials
*************************************************************

This repository contains the materials for learning about ephys data acquisition, developed as part of the Cajal Advanced Neuroscience Training Neurokit.

Building the docs remotely
########################

Pushing to the main branch of the repo triggers GitHub Actions. Gh-actions will generate a virtual environment, build the HTML pages, and then commit and push these to the 'gh-pages' branch, by following the instructions under .github/workflows/sphinx-build. Finally, if under repo settings gh pages is enabled and is set to be deployed from the 'gh-pages' branch, the docs site will be generated at https://username.github.io/reponame. To activate gh pages, go to your repo settings, Pages menu, and under "Build and Deployment", choose gh-pages in the dropdown menu. It should say "Your GitHub Pages sites is currently being built from the gh-pages branch".

Building the docs locally
##########################

Building HTML files locally allows you to preview changes before updating the live site. We recommend working with 'virtual environments' in which you can install the (versions of the) python packages that the site needs, without messing up your own installs. Here's how:

With pipenv (recommended)
-------------------------------------------------

Requirements (system)

* make

Requirements (Python 3):

* pipenv (will automatically download all the project requirements from pypi)

Create a virtual environment with pipenv (will use the Pipfile for installing the necessary packages)

.. code:: shell

   pipenv install

You can then spawn a subshell with

.. code:: shell

   pipenv shell

and then you can use ``make`` the usual way

.. code:: shell

   make html     # for html
   make latex    # for latex
   make latexpdf # for latex (will require latexpdf installed)
   make          # list all the available output format

all the outputs will be in docs folder (for html: docs/html)

Exit the virtualenv with

.. code:: exit

   exit


Troubleshooting 
######################################

No :code:`gh-pages`` branch? 
If the :code:`gh-pages`` branch is not automatically created, the build will fail and complain that there is no such branch. In that case, make an empty branch as follows: 

.. code:: empty

  git checkout --orphan gh-pages
  git reset --hard
  git commit --allow-empty -m "Initialising gh-pages branch"
  git push origin gh-pages
  git checkout main
  
Error while building? 
By default github pages `will use Jekyll <https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#static-site-generators>`_ to generate a static site. To override this, check that there is a .nojekyll file in the gh-pages branch (just an empty file called '.nojekyll'). 


Acknowledgements
####################################

This documentation's source template was taken from the `Spinal HDL <https://github.com/SpinalHDL/SpinalDoc-RTD>`_ project.

The theme is based on the `PyData Sphinx Theme <https://pydata-sphinx-theme.readthedocs.io/en/latest/>`_
