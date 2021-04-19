<!DOCTYPE html>
<html lang="fr-FR">
  <body>
    
<h1> Aide mémoire GIT</h1> <details class="custom-block details"><summary>Table des matières</summary> <p></p><div class="table-of-contents"><ul><li><a href="#personnaliser">Personnaliser</a></li><li><a href="#creer">Créer</a></li><li><a href="#modifications-locales">Modifications locales</a></li><li><a href="#historique-de-commit">Historique de Commit</a></li><li><a href="#branches-tags">Branches &amp; Tags</a></li><li><a href="#merge-rebase">Merge &amp; Rebase</a></li><li><a href="#travailler-avec-un-depots-distant">Travailler avec un dépots distant</a></li><li><a href="#annulation">Annulation</a></li><li><a href="#https-et-identifiant-sauvegarde-sous-windows">HTTPS et Identifiant sauvegardé sous Windows</a></li></ul></div><p></p></details> <h2 id="personnaliser"><a href="#personnaliser" class="header-anchor">#</a> Personnaliser</h2> <p>Définir son identité :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> config --global user.email <span class="token string">&quot;email@example.com&quot;</span>
<span class="token function">git</span> config --global user.name <span class="token string">&quot;Jeremy Selo&quot;</span>
</code></pre></div><p>Voir la configuration :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> config --list
</code></pre></div><h2 id="creer"><a href="#creer" class="header-anchor">#</a> Créer</h2> <p>Créer un nouveau dépôt local (dans le dossier courant) :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> init
</code></pre></div><p>Cloner un dépot existant :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> clone ssh://user@domain.com/repo.git
</code></pre></div><p>Créer un fichier « .gitignore » :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token comment"># Création du fichier</span>
<span class="token function">vim</span> .gitignore
<span class="token comment"># …</span>
<span class="token function">git</span> <span class="token function">add</span> .gitignore
<span class="token function">git</span> commit -m <span class="token string">&quot;Ajout gitignore&quot;</span>
</code></pre></div><p>Créer un fichier « .gitignore » en utilisant un template « Windows »:</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">curl</span> -s https://www.gitignore.io/api/windows <span class="token operator">&gt;</span> .gitignore
<span class="token function">git</span> <span class="token function">add</span> .gitignore
<span class="token function">git</span> commit -m <span class="token string">&quot;Ajout gitignore&quot;</span>
</code></pre></div><p>Créer un fichier « .gitignore » en utilisant un template « MacOS »:</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">curl</span> -s https://www.gitignore.io/api/osx <span class="token operator">&gt;</span> .gitignore
<span class="token function">git</span> <span class="token function">add</span> .gitignore
<span class="token function">git</span> commit -m <span class="token string">&quot;Ajout gitignore&quot;</span>
</code></pre></div><h2 id="modifications-locales"><a href="#modifications-locales" class="header-anchor">#</a> Modifications locales</h2> <p>Fichiers modifiés dans votre répertoire de travail :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> status
</code></pre></div><p>Modifications sur les fichiers suivis :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> <span class="token function">diff</span>
</code></pre></div><p>Ajouter tous les changements actuels au prochain commit :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> <span class="token function">add</span>
</code></pre></div><p>Ajouter tous les changements de toute l’arborescence :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> <span class="token function">add</span> --all
</code></pre></div><p>Commiter tous les changements locaux des fichiers suivis :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> commit -a
</code></pre></div><p>Commiter les modifications en attente :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> commit -m <span class="token string">'Votre message'</span>
</code></pre></div><p>Modifier le commit précédent :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> commit --amend
<span class="token comment"># ou</span>
<span class="token function">git</span> commit --am
</code></pre></div><h2 id="historique-de-commit"><a href="#historique-de-commit" class="header-anchor">#</a> Historique de Commit</h2> <p>Afficher tous les commits :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> log
</code></pre></div><p>Afficher tous les commits (uniquement l’identifiant et le texte) :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> log --oneline
</code></pre></div><p>Afficher l’historique d’un utilisateur uniquement :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> log --author<span class="token operator">=</span><span class="token string">&quot;utilisateur&quot;</span>
</code></pre></div><p>Afficher l’historique des modifications pour un fichier uniquement :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> log -p <span class="token operator">&lt;</span>fichier<span class="token operator">&gt;</span>
</code></pre></div><p>Affiche les changements (en détails) dans le fichier :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> blame <span class="token operator">&lt;</span>file<span class="token operator">&gt;</span>
</code></pre></div><h2 id="branches-tags"><a href="#branches-tags" class="header-anchor">#</a> Branches &amp; Tags</h2> <p>Lister toutes les branches :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> branch
</code></pre></div><p>Changer de branche :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> checkout <span class="token operator">&lt;</span>votre-branche<span class="token operator">&gt;</span>
</code></pre></div><p>Créer une nouvelle branche en se basant sur le HEAD :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> branch <span class="token operator">&lt;</span>votre-branche<span class="token operator">&gt;</span>
</code></pre></div><p>Créer une nouvelle branche de suivi, basée sur une branche distante :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> branch --track <span class="token operator">&lt;</span>nouvelle-branche<span class="token operator">&gt;</span> <span class="token operator">&lt;</span>branche-distante<span class="token operator">&gt;</span>
</code></pre></div><p>Supprimer une branche :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> branch -d <span class="token operator">&lt;</span>votre-branche<span class="token operator">&gt;</span>
</code></pre></div><p>Marquer le commit courant avec un tag :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> tag <span class="token operator">&lt;</span>non-du-tag<span class="token operator">&gt;</span>
</code></pre></div><h2 id="merge-rebase"><a href="#merge-rebase" class="header-anchor">#</a> Merge &amp; Rebase</h2> <p>Fusionner la branche <code>&lt;votre-branche&gt;</code> avec la master :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> checkout master
<span class="token function">git</span> merge <span class="token operator">&lt;</span>votre-branche<span class="token operator">&gt;</span>
</code></pre></div><p>⚠️ Attention ⚠️</p> <p>Jouer avec l’historique est toujours dangereux surtout si vous travaillez à plusieurs !</p> <p>Mettre à jour votre branche avec le code de la master :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> checkout <span class="token operator">&lt;</span>votre-branch<span class="token operator">&gt;</span>
<span class="token function">git</span> rebase master
</code></pre></div><p>Annuler un rebase en cours :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> rebase --abort
</code></pre></div><p>Continuer un rebase après avoir résolu des conflits :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> rebase --continue
</code></pre></div><h2 id="travailler-avec-un-depots-distant"><a href="#travailler-avec-un-depots-distant" class="header-anchor">#</a> Travailler avec un dépots distant</h2> <p>Lister tous les dépôts distants configurés :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> remote -v
</code></pre></div><p>Monter les informations d'un dépôt distant :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> remote show origin
</code></pre></div><p>Ajouter un nouveau dépôt distant, nommé &lt;remote&gt; :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> remote <span class="token function">add</span> <span class="token operator">&lt;</span>remote<span class="token operator">&gt;</span> <span class="token operator">&lt;</span>url<span class="token operator">&gt;</span>
</code></pre></div><p>Synchroniser la branche « origin » avec la master. Et indiquer origin comme le dépôt distant par défaut.</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> push -u origin master
</code></pre></div><p>Télécharger toutes les modifications d'un dépôt distant nommé &lt;remote&gt;, sans les fusionner :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> fetch <span class="token operator">&lt;</span>remote<span class="token operator">&gt;</span>
</code></pre></div><p>Télécharger les modifications et les fusionner directement dans le HEAD :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> remote pull <span class="token operator">&lt;</span>remote<span class="token operator">&gt;</span> <span class="token operator">&lt;</span>url<span class="token operator">&gt;</span>
</code></pre></div><p>Fusionner les modifications de la <code>master</code> distante sur la branche courante :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> pull origin master
</code></pre></div><p>Récupérer toutes les modifications du HEAD dans le dépôt local :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> pull
<span class="token comment"># ou</span>
<span class="token function">git</span> pull origin
</code></pre></div><p>Publier les modifications locales sur un dépôt distant :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> push
ou
<span class="token function">git</span> push remote <span class="token operator">&lt;</span>remote<span class="token operator">&gt;</span> <span class="token operator">&lt;</span>branch<span class="token operator">&gt;</span>
</code></pre></div><p>Publier les tags :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> push --tags
</code></pre></div><h2 id="annulation"><a href="#annulation" class="header-anchor">#</a> Annulation</h2> <p>Annuler le dernier <code>git add</code> :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> reset HEAD
</code></pre></div><p>Annuler les modifications locales d'un fichier spécifique :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> checkout HEAD <span class="token operator">&lt;</span>file<span class="token operator">&gt;</span>
</code></pre></div><p>Annuler un commit (création d’un commit avec les modifications inverses) :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> revert <span class="token operator">&lt;</span>commit<span class="token operator">&gt;</span>
</code></pre></div><p>Placer le pointeur du HEAD sur un commit précédent.
Conserve toutes les modifications effectuées depuis :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> reset <span class="token operator">&lt;</span>commit<span class="token operator">&gt;</span>
</code></pre></div><p>⚠️ Annuler toutes les modifications dans le répertoire de travail :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> reset --hard HEAD
</code></pre></div><p>⚠️ Placer le pointeur du HEAD sur un commit précédent.
Annule toutes les modifications effectuées depuis :</p> <div class="language-sh extra-class"><pre class="language-sh"><code><span class="token function">git</span> reset --hard <span class="token operator">&lt;</span>commit<span class="token operator">&gt;</span>
</code></pre></div><h2 id="https-et-identifiant-sauvegarde-sous-windows"><a href="#https-et-identifiant-sauvegarde-sous-windows" class="header-anchor"></footer> 
