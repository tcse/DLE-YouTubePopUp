# YouTubePopUp
Запуск ссылок на YouTube в модальном окне. Плагин для DLE 13 и выше.

Доработка плагина https://github.com/tcse/YouTube_PopUp для использования в шаблона DLE CMS. Например для RSS информеров в которых используются ссылки на youtube ролики.

## Установка

В файле main.tpl найти место подключения jQuery, напоминаю, что он уже есть в любой версии DLE. 
Обычно он загружается переменной {jsfiles}{AJAX} если скрипты вынесены в конец файла.

Или перед закрывающим тегом

    </body>


Если используется классический способ подключения стилей и JS.

После jQuery Вставить:


    {* YouTube_PopUp *}
    <link rel="stylesheet" type="text/css" href="{THEME}/assets/youtubepopup/YouTubePopUp.css">
    <script type="text/javascript" src="{THEME}/assets/youtubepopup/YouTubePopUp.jquery.js"></script>
    <script type="text/javascript">
      jQuery(function(){
          jQuery("a.bla-1").YouTubePopUp();
          jQuery("a.bla-2").YouTubePopUp( { autoplay: 0 } ); // Disable autoplay
      });
    </script>



Если же необходимо добавить запуск окна с плеером YouTube для всех ссылок на сайте, которые ведут на https://www.youtube.com/ тогда дополнительно добавьте перед закрывающим тегом

    </body>


    $('a[href^="https://www.youtube.com/watch?"]').addClass("bla-2");

и получиться что-то вроде


    <script>
        $('a[href^="https://www.youtube.com/watch?"]').addClass("bla-2");
        $('a[href^="https://youtu.be/"]').addClass("bla-1");
    </script>

Что бы на картинки роликов из полной новости в шаблоне [b]fullstory.tpl[/b] автоматически накладывались иконки плеера, необходимо тег {full-story} обернуть в класс

    <div class="full-content">{full-story}</div>
  
  


Пользуйтесь.
