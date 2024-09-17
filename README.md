# AulaBancoMYSQL
-- Criação do banco de dados
CREATE DATABASE aulabanco;

-- Seleção do banco de dados
USE aulabanco;

-- Tabela 1: Alunos
CREATE TABLE Alunos (
    aluno_id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    data_nascimento DATE,
    email VARCHAR(100),
    telefone VARCHAR(15)
);

-- Tabela 2: Cursos
CREATE TABLE Cursos (
    curso_id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    descricao TEXT,
    carga_horaria INT
);

-- Tabela 3: Matriculas
CREATE TABLE Matriculas (
    matricula_id INT AUTO_INCREMENT PRIMARY KEY,
    aluno_id INT,
    curso_id INT,
    data_matricula DATE,
    FOREIGN KEY (aluno_id) REFERENCES Alunos(aluno_id),
    FOREIGN KEY (curso_id) REFERENCES Cursos(curso_id)
);

-- Tabela 4: Professores
CREATE TABLE Professores (
    professor_id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    departamento VARCHAR(50),
    email VARCHAR(100)
);

-- Tabela 5: Aulas
CREATE TABLE Aulas (
    aula_id INT AUTO_INCREMENT PRIMARY KEY,
    curso_id INT,
    professor_id INT,
    data_aula DATE,
    horario TIME,
    FOREIGN KEY (curso_id) REFERENCES Cursos(curso_id),
    FOREIGN KEY (professor_id) REFERENCES Professores(professor_id)
);

-- Inserindo dados na tabela Alunos
INSERT INTO Alunos (nome, data_nascimento, email, telefone) VALUES
('Rafael Moraes', '2007-06-19', 'rafael@gmail.com', '51999999999'),
('Junior Lima', '2006-01-28', 'juninho@gmail.com', '51987654321'),
('Lucas Brito', '2007-11-16', 'luquinhas@gmail.com', '5191234567'),
('Flavia Silva', '2008-11-08', 'flavia@gmail.com', '5192837465'),
('Theo Vigano', '2007-02-05', 'theo@gmail.com', '51978901234');

-- Inserindo dados na tabela Cursos
INSERT INTO Cursos (nome, descricao, carga_horaria) VALUES
('Matemática', 'Curso de matemática básica e avançada', 60),
('Educação Física', 'Curso sobre educação física e futebol', 45),
('Programação', 'Curso de introdução à programação', 80),
('Fisíca', 'Curso de física clássica e moderna', 70),
('Psicologia', 'Curso de psicologia e organização', 65);

-- Inserindo dados na tabela Matriculas
INSERT INTO Matriculas (aluno_id, curso_id, data_matricula) VALUES
(1, 3, '2024-01-10'),
(2, 1, '2024-01-15'),
(3, 4, '2024-01-20'),
(4, 2, '2024-01-25'),
(5, 5, '2024-02-01');

-- Inserindo dados na tabela Professores
INSERT INTO Professores (nome, departamento, email) VALUES
('Sérgio', 'Matemática', 'serginho@gmail.com'),
('Carlos Rei', 'Educação Física', 'carlos.rei@gmail.com'),
('Éder de Rosso', 'Programação', 'eder.rosso@gmail.com'),
('André', 'Física', 'andre@gmail.com'),
('Cristiane Souza', 'Psicologia', 'cristiane.souza@gmail.com');

-- Inserindo dados na tabela Aulas
INSERT INTO Aulas (curso_id, professor_id, data_aula, horario) VALUES
(1, 1, '2024-02-05', '09:00:00'),
(2, 2, '2024-02-06', '10:00:00'),
(3, 3, '2024-02-07', '14:00:00'),
(4, 4, '2024-02-08', '11:00:00'),
(5, 5, '2024-02-09', '13:00:00');


-- Atualizando dados na tabela Alunos
UPDATE Alunos SET telefone = '111223344' WHERE aluno_id = 1;
UPDATE Alunos SET email = 'junior@outlook.com' WHERE aluno_id = 2;
UPDATE Alunos SET nome = 'Carmem Raquel' WHERE aluno_id = 3;
UPDATE Alunos SET telefone = '321654987' WHERE aluno_id = 4;
UPDATE Alunos SET data_nascimento = '1997-10-15' WHERE aluno_id = 5;

-- Atualizando dados na tabela Cursos
UPDATE Cursos SET descricao = 'Curso de matemática abrangente' WHERE curso_id = 1;
UPDATE Cursos SET carga_horaria = 50 WHERE curso_id = 2;
UPDATE Cursos SET nome = 'Programação Avançada' WHERE curso_id = 3;
UPDATE Cursos SET descricao = 'Curso de física experimental e teórica' WHERE curso_id = 4;
UPDATE Cursos SET carga_horaria = 70 WHERE curso_id = 5;

-- Atualizando dados na tabela Matriculas
UPDATE Matriculas SET data_matricula = '2024-01-12' WHERE matricula_id = 1;
UPDATE Matriculas SET data_matricula = '2024-01-18' WHERE matricula_id = 2;
UPDATE Matriculas SET aluno_id = 4 WHERE matricula_id = 3;
UPDATE Matriculas SET curso_id = 1 WHERE matricula_id = 4;
UPDATE Matriculas SET data_matricula = '2024-02-03' WHERE matricula_id = 5;

-- Atualizando dados na tabela Professores
UPDATE Professores SET departamento = 'Matemática Aplicada' WHERE professor_id = 1;
UPDATE Professores SET email = 'reizinho@gmail.com' WHERE professor_id = 2;
UPDATE Professores SET nome = 'Felipe Mendes Silva' WHERE professor_id = 3;
UPDATE Professores SET departamento = 'Física Experimental' WHERE professor_id = 4;
UPDATE Professores SET email = 'renato.lima@outlook.com' WHERE professor_id = 5;

-- Atualizando dados na tabela Aulas
UPDATE Aulas SET horario = '10:30:00' WHERE aula_id = 1;
UPDATE Aulas SET data_aula = '2024-02-07' WHERE aula_id = 2;
UPDATE Aulas SET professor_id = 2 WHERE aula_id = 3;
UPDATE Aulas SET horario = '11:30:00' WHERE aula_id = 4;
UPDATE Aulas SET curso_id = 2 WHERE aula_id = 5;


-- Excluindo dados da tabela Alunos
DELETE FROM Aluno WHERE aluno_id = 1;
DELETE FROM Aluno WHERE aluno_id = 2;
DELETE FROM Aluno WHERE aluno_id = 3;
DELETE FROM Aluno WHERE aluno_id = 4;
DELETE FROM Aluno WHERE aluno_id = 5;

-- Excluindo dados da tabela Cursos
DELETE FROM Cursos WHERE curso_id = 1;
DELETE FROM Cursos WHERE curso_id = 2;
DELETE FROM Cursos WHERE curso_id = 3;
DELETE FROM Cursos WHERE curso_id = 4;
DELETE FROM Cursos WHERE curso_id = 5;

-- Excluindo dados da tabela Matriculas
DELETE FROM Matriculas WHERE matricula_id = 1;
DELETE FROM Matriculas WHERE matricula_id = 2;
DELETE FROM Matriculas WHERE matricula_id = 3;
DELETE FROM Matriculas WHERE matricula_id = 4;
DELETE FROM Matriculas WHERE matricula_id = 5;

-- Excluindo dados da tabela Professores
DELETE FROM Professores WHERE professor_id = 1;
DELETE FROM Professores WHERE professor_id = 2;
DELETE FROM Professores WHERE professor_id = 3;
DELETE FROM Professores WHERE professor_id = 4;
DELETE FROM Professores WHERE professor_id = 5;

-- Excluindo dados da tabela Aulas
DELETE FROM Aulas WHERE aula_id = 1;
DELETE FROM Aulas WHERE aula_id = 2;
DELETE FROM Aulas WHERE aula_id = 3;
DELETE FROM Aulas WHERE aula_id = 4;
DELETE FROM Aulas WHERE aula_id = 5;

select * from Professores;
