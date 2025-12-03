# Todo App (Jetpack Compose)

Aplicativo Android simples de lista de tarefas desenvolvido com Jetpack Compose e MVVM.

## O que o app faz
- Exibe uma lista de tarefas iniciais carregadas em memória.
- Permite adicionar uma nova tarefa digitando o título e tocando em **Add**.
- Permite apagar qualquer tarefa pelo ícone de lixeira.
- A lista é armazenada apenas em memória durante a execução (sem persistência após fechar o app).

A tela principal (`TodoListPage`) usa Compose para renderizar a lista e observa o estado exposto pelo `TodoViewModel`, que delega operações de adicionar e remover ao `TodoManager`.

## Pré-requisitos
- Android SDK (compileSdk 34, minSdk 26, targetSdk 34).
- JDK 17+ (recomendado para Android Gradle Plugin 8.2).
- Android Studio Hedgehog ou mais recente (suporta AGP 8.2 e Compose).

## Versões das principais dependências
- Gradle Wrapper: **8.2** (`gradle/wrapper/gradle-wrapper.properties`).
- Android Gradle Plugin: **8.2.0** (`build.gradle.kts`).
- Kotlin: **1.9.0** (`build.gradle.kts`).
- Jetpack Compose BOM: **2023.08.00** (`app/build.gradle.kts`).
- Material 3: da BOM 2023.08.00 (`androidx.compose.material3:material3`).
- Lifecycle Runtime KTX: **2.7.0**.
- Activity Compose: **1.8.2**.

## Como rodar exatamente
1. **Instale dependências**: certifique-se de que o Android SDK 34 está instalado e configurado via `ANDROID_HOME`/`ANDROID_SDK_ROOT`.
2. **Sincronize o projeto**: abra a pasta `TOdo` no Android Studio e aguarde o download das dependências.
3. **Executar via linha de comando** (opcional):
   ```bash
   ./gradlew clean assembleDebug
   ```
4. **Iniciar o app**:
   - No Android Studio, selecione um emulador ou dispositivo físico e clique em **Run > Run 'app'**.
   - Ou, após o passo 3, instale o APK gerado em `app/build/outputs/apk/debug/app-debug.apk` com `adb install -r app/build/outputs/apk/debug/app-debug.apk`.

## Estrutura principal
- `app/src/main/java/np/com/bimalkafle/todoapp/MainActivity.kt`: inicializa o tema e exibe `TodoListPage`.
- `app/src/main/java/np/com/bimalkafle/todoapp/TodoListPage.kt`: UI Compose com campo de entrada, botão de adicionar e lista com exclusão.
- `app/src/main/java/np/com/bimalkafle/todoapp/TodoViewModel.kt`: expõe a lista de tarefas como `LiveData` e coordena operações.
- `app/src/main/java/np/com/bimalkafle/todoapp/TodoManager.kt`: fonte em memória das tarefas (inclui dados mockados).
- `app/src/main/java/np/com/bimalkafle/todoapp/Todo.kt`: modelo de dados da tarefa.

## Observações
- Os dados são apenas para demonstração; para persistência real seria necessário integrar banco local (Room) ou backend.
- O aplicativo usa Material 3 e o tema padrão definido em `ui/theme`.
