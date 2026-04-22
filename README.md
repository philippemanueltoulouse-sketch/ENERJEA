<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ENERJEA</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
:root{--primary:#2563eb;--dark:#0f172a;--text:#1e293b;--light:#f8fafc;--border:#e2e8f0}
body{margin:0;font-family:'Inter',sans-serif;color:var(--text)}
header{position:fixed;top:0;width:100%;background:white;border-bottom:1px solid var(--border);padding:15px 30px;display:flex;justify-content:space-between;align-items:center;z-index:1000}
.hero{padding:160px 20px 120px;text-align:center;background:linear-gradient(135deg,#0f172a,#1e3a8a);color:white}
h1{font-size:52px;margin-bottom:20px}
.btn{background:var(--primary);color:white;padding:16px 30px;border-radius:12px;text-decoration:none;font-weight:600;display:inline-block;box-shadow:0 15px 40px rgba(37,99,235,0.3)}
section{padding:80px 20px;max-width:1100px;margin:auto}
.grid{display:grid;gap:25px}.grid-3{grid-template-columns:repeat(auto-fit,minmax(280px,1fr))}
.card{padding:30px;border-radius:16px;background:white;box-shadow:0 15px 40px rgba(0,0,0,0.05);border:1px solid var(--border)}
.section-light{background:var(--light)}
.cta{background:linear-gradient(135deg,#2563eb,#1d4ed8);color:white;text-align:center;padding:80px 20px;border-radius:20px}
.sticky{position:fixed;bottom:20px;right:20px}
.progress{font-size:14px;color:#64748b;margin-top:10px}
input,select{width:100%;padding:14px;border-radius:10px;border:1px solid var(--border);margin-bottom:10px}
</style>
</head>

<body>

<header>
<div style="display:flex;align-items:center;gap:10px">
<img src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEASABIAAD/2wBDAAMCAgICAgMCAgIDAwMDBAYEBAQEBAgGBgUGCQgKCgkICQkKDA8MCgsOCwkJDRENDg8Q" style="height:40px">
<strong>ENERJEA</strong>
</div>
<a href="#contact" class="btn">Simulation gratuite</a>
</header>

<section class="hero">
<h1>Ne bloquez plus vos projets à cause du cash</h1>
<p>Financez jusqu’à 100% de vos équipements grâce au préfinancement CEE</p>
<a href="#contact" class="btn">Tester mon éligibilité</a>
</section>

<section>
<h2>Pourquoi ça change tout</h2>
<div class="grid grid-3">
<div class="card"><strong>ZERO AVANCE, ZERO CONTRAINTE</strong><br><br>Démarrez votre projet énergétique sans attendre. Nous vous avançons vos CEE, pour un projet sans pression sur votre trésorerie.</div>
<div class="card"><strong>Tranquillité d’esprit</strong><br><br>Simplifiez-vous vos démarches, sécurisez vos flux financiers et concentrez-vous sur l’essentiel : la réussite de votre projet !<br><br>Nous prenons en charge le règlement de vos acomptes fournisseurs !<br>Confiez-nous la gestion complète de votre dossier CEE.</div>
<div class="card"><strong>ROI Accéléré</strong><br><br>Votre projet devient un véritable levier de croissance.<br>Vous gagnez en visibilité et rendez indolore votre mise en conformité réglementaire.<br><br>N’attendez plus, accordez-vous le plaisir d’agir de suite !</div>
</div>
</section>

<section>
<h2>Comment ça marche</h2>
<ol>
<li>Simulation en 30 secondes</li>
<li>Validation rapide : proposition sous 24h et accord sous 3 jours ouvrés</li>
<li><strong>Avance immédiate des CEE</strong> : déblocage des fonds après accord</li>
<li><strong>Lancement du chantier</strong> : paiement des acomptes fournisseurs</li>
</ol>
</section>

<section id="contact" class="section-light">
<h2>Simulation instantanée</h2>

<form id="form">

<div class="step">
<select name="type_projet" required>
<option value="">Type de projet</option>
<option>Industriel</option>
<option>Tertiaire</option>
<option>Résidentiel</option>
</select>
</div>

<div class="step" style="display:none">
<input name="montant" placeholder="Montant à financer" required>
<input name="duree" placeholder="Durée chantier" required>
<input name="cee" placeholder="Montant CEE estimé" required>
</div>

<div class="step" style="display:none">
<input name="societe" placeholder="Raison sociale" required>
<input name="nom" placeholder="Nom prénom" required>
<input name="email" type="email" placeholder="Email" required>
<input name="telephone" placeholder="Téléphone (optionnel)">
</div>

<label style="font-size:14px">
<input type="checkbox" required> J’accepte les 
<a href="https://enerjea.com/mentions-legales-enerjea/" target="_blank">mentions légales</a>
</label>

<button type="button" onclick="nextStep()" class="btn">Continuer</button>
<div class="progress" id="progress">Étape 1/3</div>
</form>
</section>

<section><div class="cta"><h2>Recevez votre estimation en moins de 24h</h2></div></section>

<div class="sticky"><a href="#contact" class="btn">Simulation gratuite</a></div>

<footer style="text-align:center;padding:40px;color:#64748b">© 2026 - ENERJEA</footer>

<script>
let step=0;
const steps=document.querySelectorAll('.step');
const progress=document.getElementById('progress');

function nextStep(){
if(step<steps.length-1){
steps[step].style.display='none';
step++;
steps[step].style.display='block';
progress.innerText=`Étape ${step+1}/3`;
}else{
sendToGoogleSheets();
alert('Merci ! Votre demande a été envoyée.');
}
}

function sendToGoogleSheets(){
const scriptURL = 'https://script.google.com/macros/s/TON_SCRIPT_ID/exec';
const form = document.getElementById('form');
const formData = new FormData(form);

fetch(scriptURL, {
method: 'POST',
body: formData,
mode: 'no-cors'
});
}

/*
⚠️ IMPORTANT : AJOUTER L'EMAIL AUTOMATIQUE DANS GOOGLE APPS SCRIPT

Dans ton script Google Apps Script, remplace ton code par :

function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  
  sheet.appendRow([
    new Date(),
    e.parameter.type_projet,
    e.parameter.montant,
    e.parameter.duree,
    e.parameter.cee,
    e.parameter.societe,
    e.parameter.nom,
    e.parameter.email,
    e.parameter.telephone
  ]);

  MailApp.sendEmail(
    "philippemanueltoulouse@gmail.com",
    "Nouveau lead ENERJEA",
    "Nouveau lead reçu :

" +
    "Projet : " + e.parameter.type_projet + "
" +
    "Montant : " + e.parameter.montant + "
" +
    "Durée : " + e.parameter.duree + "
" +
    "CEE : " + e.parameter.cee + "
" +
    "Société : " + e.parameter.societe + "
" +
    "Nom : " + e.parameter.nom + "
" +
    "Email : " + e.parameter.email + "
" +
    "Téléphone : " + e.parameter.telephone
  );

  return ContentService.createTextOutput("OK");
}
*/);
}
</script>

</body>
</html>
