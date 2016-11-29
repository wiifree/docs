Flash
#####

.. php:namespace:: Cake\View\Helper

.. php:class:: FlashHelper(View $view, array $config = [])

FlashHelper bieten eine Möglichkeit um Flashnachrichten anzuzeigen die gesetzt wurden in
``$_SESSION`` von :doc:`FlashComponent </controllers/components/flash>`.
:doc:`FlashComponent </controllers/components/flash>` und FlashHelper
benutzen in erster Linie Elemente um Flash Nachrichten zu erstellen. Flash Elemente finden Sie unter
dem Verzeichnis **src/Template/Element/Flash** .  Sie werden feststellen das CakePHP's Apps
Vorlagen mit zwei Flash Elementen kommt: **success.ctp** und **error.ctp**.

Anzeigen von Flash Nachrichten
========================

Um eine Flash Nachricht anzuzeigen, können Sie einfach FlashHelper's ``render()``
methode benutzen::

    <?= $this->Flash->render() ?>

Als Standart, benutzt CakePHP eine "flash" Taste für Flash Nachrichten in einer Session. Aber, wenn
Sie bei der Einstellung der Flash Nachricht in
:doc:`FlashComponent </controllers/components/flash>`, eine Taste angegeben haben, können Sie jedoch festlegen, welche Flash-Taste zu rendern ist::

    <?= $this->Flash->render('other') ?>

Sie können auch alle Optionen überschreiben die in der Flash Componente gesetzt wurden::

    // In ihrem Controller
    $this->Flash->set('Der Benutzer wurde gespeichert.', [
        'element' => 'erfolgreich'
    ]);

    // In ihrer View: Wird great_success.ctp benutzt anstatt succcess.ctp
    <?= $this->Flash->render('flash', [
        'element' => 'great_success'
    ]);

.. note::

    Wenn Sie eigene Flash Nachrichten erstellen, stellen Sie sicher das HTML
    alle Benutzerdaten kodiert. CakePHP werden Flash-Nachrichtenparameter nicht entgehen.

.. versionadded:: 3.1

    Die :doc:`FlashComponent </controllers/components/flash>` stapelt jetzt Nachrichten.
    Wenn Sie mehrere Flash Nachrichten erstellen, beim benutzten von
    ``render()``, jede Nachricht wird in ihrem eigenen Element gerendert in der Sie gesetzt wurde.

Weitere Informationen zu den verfügbaren Arrayoptionen finden Sie im
:doc:`FlashComponent </controllers/components/flash>` Bereich.

Routing Prefix und Flash Messages
=================================

.. versionadded:: 3.0.1

Wenn Sie ein Routing-Präfix konfiguriert haben, können Sie jetzt ihre Flash Elemente in 
**src/Template/{Prefix}/Element/Flash** ablegen. Auf diese Weise können Sie mehrere
Spezifische Nachrichten-Layouts für jeden Teil Ihrer Anwendung haben. Zum Beispiel mit
Verschiedene Layouts für Ihren Front-End und Admin-Bereich.

Flash Nachrichten und Themes
=========================

Der FlashHelper benutzt normale Elemente um Nachrichten anzuzeigen und wird daher
jedem Theme folgen das Sie angegeben haben. Also wenn ihr Theme eine 
**src/Template/Element/Flash/error.ctp** Datei beinhaltet wird Sie benutzt, so wie
mit jedem Element und jeder Ansicht.
